# UML model specification

## Product
Represents a medicine or other stocked pharmacy item.
Attributes: - productId: String, - name: String, - unitPrice: Decimal, - quantityInStock: Integer, - reorderLevel: Integer
Operations: + updatePrice(newPrice: Decimal): void, + adjustStock(quantityChange: Integer): void, + isLowStock(): Boolean

## Category
Groups products by a pharmacy category.
Attributes: - categoryId: String, - name: String, - description: String
Operations: + updateDescription(description: String): void, + getProductCount(): Integer

## Supplier
Stores details of a business that supplies pharmacy products.
Attributes: - supplierId: String, - name: String, - phone: String, - email: String
Operations: + updateContact(phone: String, email: String): void

## PurchaseOrder
Records an order placed with a supplier.
Attributes: - orderId: String, - orderDate: Date, - status: OrderStatus
Operations: + addLine(product: Product, quantity: Integer, cost: Decimal): void, + calculateTotal(): Decimal, + markReceived(): void

## PurchaseOrderLine
Records one product and quantity within a purchase order.
Attributes: - quantity: Integer, - unitCost: Decimal
Operations: + getLineTotal(): Decimal

## Sale
Records a customer transaction processed by an employee.
Attributes: - saleId: String, - saleDateTime: DateTime, - paymentMethod: String, - status: SaleStatus
Operations: + addLine(product: Product, quantity: Integer): void, + calculateTotal(): Decimal, + completeSale(): Boolean

## SaleLine
Records one product, quantity and sale price within a sale.
Attributes: - quantity: Integer, - unitPrice: Decimal
Operations: + getLineTotal(): Decimal

## Customer
Stores optional customer details for a sale.
Attributes: - customerId: String, - fullName: String, - phone: String
Operations: + updatePhone(phone: String): void

## Employee
Represents a staff member who records and manages transactions.
Attributes: - employeeId: String, - fullName: String, - role: String
Operations: + recordSale(): Sale, + createPurchaseOrder(supplier: Supplier): PurchaseOrder

## OrderStatus («enumeration»)
Lifecycle state of a purchase order.
Values: PENDING, RECEIVED, CANCELLED

## SaleStatus («enumeration»)
Lifecycle state of a sale.
Values: PENDING, COMPLETED, CANCELLED

## Relationships
- Category (1) — Product (0..*): categorises; association
- Supplier (1) — PurchaseOrder (0..*): supplies orders; association
- PurchaseOrder (1) — PurchaseOrderLine (1..*): contains; composition, filled diamond at PurchaseOrder
- Product (1) — PurchaseOrderLine (0..*): ordered as; association
- Employee (1) — PurchaseOrder (0..*): creates; association
- Employee (1) — Sale (0..*): records; association
- Customer (0..1) — Sale (0..*): optional customer; association
- Sale (1) — SaleLine (1..*): contains; composition, filled diamond at Sale
- Product (1) — SaleLine (0..*): sold as; association
- PurchaseOrder → OrderStatus: dependency (dashed arrow), type of `status`
- Sale → SaleStatus: dependency (dashed arrow), type of `status`
