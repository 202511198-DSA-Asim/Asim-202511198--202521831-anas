# Lecturer questions and revision sheet

## Likely lecturer questions with model answers

1. **What is the purpose of your project?**  
   It models the main records and relationships needed for basic pharmacy inventory, purchasing, and sales management.

2. **Why did you choose a pharmacy system?**  
   It is a realistic small-business domain with meaningful stock, supplier, purchase, sale, and staff relationships while remaining manageable.

3. **What is a UML class?**  
   A class describes a type of object through its attributes (data) and operations (behaviour).

4. **Why does Product have quantityInStock?**  
   The system needs to represent current available stock and identify items at or below the reorder level.

5. **Why is Category separate from Product?**  
   Many products can share one category, and category information should not be duplicated on every product.

6. **Why is PurchaseOrderLine a separate class?**  
   An order contains multiple products, and each product line has its own quantity and unit cost. Those attributes belong to the line, not just the order or product.

7. **Why is SaleLine a separate class?**  
   Each line stores the quantity and price charged for a specific product in a particular sale.

8. **Explain multiplicity 1 to 0..* for Category–Product.**  
   One category can classify no products or many products; every product belongs to exactly one category under our assumptions.

9. **Why is a purchase order connected to one supplier?**  
   The model assumes each order is placed with one supplier. If orders could combine suppliers, the design would need to change.

10. **Why does a Sale contain 1..* SaleLines rather than 0..*?**  
    A completed sale must contain at least one item. An implementation might temporarily create an empty draft, but that lifecycle is outside this simplified model.

11. **What does composition mean here?**  
    It expresses a strong whole-part relationship: the transaction line is treated as part of its purchase order or sale and does not exist independently in the business model.

12. **Where does the filled diamond go?**  
    At the owner/whole end: PurchaseOrder for PurchaseOrderLine, and Sale for SaleLine.

13. **Why not use inheritance?**  
    The requirements do not establish a genuine “is-a” hierarchy. Adding inheritance only to show the symbol would make the model less justified.

14. **Why is Customer optional on Sale?**  
    A walk-in customer may buy an item without providing identifying information. A sale therefore has zero or one customer.

15. **Why can a Customer be associated with many Sales?**  
    A returning customer may make multiple purchases over time.

16. **Why is unitPrice stored in SaleLine as well as Product?**  
    Product.unitPrice represents the current price; SaleLine.unitPrice preserves the price used for that historical transaction.

17. **What does `-` mean? What does `+` mean?**  
    `-` means private visibility; `+` means public visibility.

18. **What does 0..1 mean?**  
    Zero or one instance: participation is optional but cannot involve more than one.

19. **What does 1..* mean?**  
    At least one instance, possibly many.

20. **Why is Employee associated with Sale?**  
    Each sale is attributed to the employee who records it, providing transaction accountability in the model.

21. **Does the diagram prove the software is implemented?**  
    No. It is a design model for the proposed system; no functioning application is claimed.

22. **What important features are excluded?**  
    Prescription validation, insurance, tax/accounting integration, delivery, barcode scanning, multi-branch synchronisation, and deployment.

23. **What constraints should a real implementation validate?**  
    Positive transaction quantities, non-negative prices and costs, valid stock adjustments, and consistency between transaction totals and line totals.

24. **Why is there no separate Inventory class?**  
    The current scope uses a single stock quantity on Product. Multiple warehouses, stock movements, batches, and expiry dates would justify a richer inventory model.

25. **What would you improve if the project expanded?**  
    Add batch/expiry tracking, returns, discounts/taxes, permissions, audit logs, and multi-branch stock only after gathering requirements.

26. **Why are OrderStatus and SaleStatus enumerations?**  
    A status can only take a fixed set of values (e.g. PENDING, RECEIVED/COMPLETED, CANCELLED). An enumeration defines them instead of allowing any free text.

27. **Why is createPurchaseOrder only on Employee?**  
    An employee is the person who creates an order, and the operation takes the Supplier as a parameter. Supplier only manages its own contact details.

28. **Why is the Employee–Sale line drawn with a bend?**  
    It is routed at right angles so that it does not cross other classes. The meaning is still one Employee to zero or many Sales.

## Quick revision sheet
- Class = name + attributes + operations.
- `-` private; `+` public.
- `1` exactly one; `0..1` optional one; `0..*` zero or many; `1..*` one or many.
- Association = general domain link.
- Composition = strong whole-part; filled diamond at the whole.
- `PurchaseOrder` ◆— `PurchaseOrderLine`; `Sale` ◆— `SaleLine`.
- Line-item classes hold their own quantity and transaction-specific price/cost.
- Each Product belongs to one Category.
- Each Sale and PurchaseOrder has one Employee.
- Customer association on Sale is optional.
- OrderStatus and SaleStatus are «enumeration» types, joined by dashed dependency arrows.
- Model only the agreed scope; do not claim unmodelled features.
