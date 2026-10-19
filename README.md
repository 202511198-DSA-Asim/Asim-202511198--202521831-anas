# Community Pharmacy Inventory and Sales Management System

**Institution:** Kigali Independent University (ULK)  
**Assignment:** UML Class Diagram Modelling Assignment  
**Group members:** Anas Yaseir (202512831) and Asim Mohamed (202511198)

## Overview
This repository contains a UML design proposal for a community pharmacy inventory and sales management system. It models products, categories, suppliers, purchase orders, sales, transaction line items, customers, and employees. This is a modelling/documentation project; it is not a deployed application.

## Problem statement
Paper-based or disconnected records can make it difficult to trace stock, supplier orders, sales, and the employees responsible for transactions. The proposed model defines a consistent set of classes and relationships for these records.

## Scope
**Included:** product and category records, stock quantity and reorder level, suppliers, purchase orders and order lines, sales and sale lines, employee attribution, optional customer association, totals, and low-stock checking.

**Excluded:** prescription/clinical workflows, insurance, accounting/tax integration, delivery, barcode scanning, multi-branch synchronisation, authentication implementation, and deployment.

## Main classes
- **Product:** Represents a medicine or other stocked pharmacy item.
- **Category:** Groups products by a pharmacy category.
- **Supplier:** Stores details of a business that supplies pharmacy products.
- **PurchaseOrder:** Records an order placed with a supplier.
- **PurchaseOrderLine:** Records one product and quantity within a purchase order.
- **Sale:** Records a customer transaction processed by an employee.
- **SaleLine:** Records one product, quantity and sale price within a sale.
- **Customer:** Stores optional customer details for a sale.
- **Employee:** Represents a staff member who records and manages transactions.
- **OrderStatus / SaleStatus** («enumeration»): the allowed status values of a purchase order and of a sale.

## Relationship summary
- `Category` — `Product`: categorises; multiplicities `1` / `0..*`; association.
- `Supplier` — `PurchaseOrder`: supplies orders; multiplicities `1` / `0..*`; association.
- `PurchaseOrder` — `PurchaseOrderLine`: contains; multiplicities `1` / `1..*`; composition (filled diamond at PurchaseOrder).
- `Product` — `PurchaseOrderLine`: ordered as; multiplicities `1` / `0..*`; association.
- `Employee` — `PurchaseOrder`: creates; multiplicities `1` / `0..*`; association.
- `Employee` — `Sale`: records; multiplicities `1` / `0..*`; association.
- `Customer` — `Sale`: optional customer; multiplicities `0..1` / `0..*`; association.
- `Sale` — `SaleLine`: contains; multiplicities `1` / `1..*`; composition (filled diamond at Sale).
- `Product` — `SaleLine`: sold as; multiplicities `1` / `0..*`; association.
- `PurchaseOrder` → `OrderStatus` and `Sale` → `SaleStatus`: dependency (dashed arrow) for the `status` attribute type.

## Repository structure
```text
uml-class-diagram-assignment/
├── README.md
├── documentation/
│   ├── report_1_project_description.pdf
│   └── report_2_uml_class_diagram.pdf
├── diagrams/
│   ├── uml_class_diagram.drawio
│   ├── uml_class_diagram.png
│   ├── uml_class_diagram.pdf
│   └── uml_model_specification.md
└── guides/
    ├── handwritten_summary_and_drawing_guide.md
    ├── lecturer_questions_and_revision.md
    └── compliance_and_quality_audit.md
```

## Deliverables
- Project Description Report (PDF)
- UML Class Diagram Report (PDF)
- Editable draw.io source
- PNG diagram export and PDF diagram export
- Handwriting guide, presentation questions, revision notes, and compliance checklist

## How to edit the diagram
Open `diagrams/uml_class_diagram.drawio` in https://app.diagrams.net/ (draw.io). If you change it, export a fresh PNG/PDF.

## Submission reminder
Upload the reports, diagram source and exports, and README to a GitHub repository. Ensure the lecturer can access it, then submit the repository URL through the Google Form specified in the assignment. Also submit the handwritten summary and complete hand-drawn diagram on paper. Do not submit a printed copy as the hand-drawn diagram.
