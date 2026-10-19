# Compliance checklist and quality audit (revised)

## Lecturer-specific mandatory requirements

| Requirement | Evidence | Status | Action |
|---|---|---|---|
| Business idea selected and described | Report 1, README | Pass | Confirm group agrees with selected idea |
| Project scope and problem statement | Report 1, README | Pass | Check wording before upload |
| Report 1 PDF | documentation/report_1_project_description.pdf | Pass | Open and proofread |
| Report 2 PDF | documentation/report_2_uml_class_diagram.pdf | Pass | Regenerated with the corrected diagram on a landscape page |
| Classes, attributes, operations | Diagram and Report 2 | Pass | Diagram and Report 2 are generated from the same model |
| Relationships and multiplicities | Report 2 and diagram | Pass | All 9 relationships have multiplicities at both ends; no line crosses a class box or another line (checked by script) |
| Electronic diagram | diagrams/uml_class_diagram.png and .pdf | Pass | PDF is vector: zoom to check |
| Editable source | diagrams/uml_class_diagram.drawio | Not Yet Verified | File is valid XML; open it once in diagrams.net and confirm it looks like the PNG |
| README.md | Root README | Pass | Ensure paths match uploaded repository |
| GitHub repository and accessibility | External account action | Not Yet Verified | Create repository, upload files, test in a logged-out window |
| Google Form repository link | Lecturer's form | Not Yet Verified | Submit https://forms.gle/Bt3DVff4oFb5dxe17 with both names, IDs and the repository URL |
| Handwritten summary | To be written by students | Not Yet Verified | Copy guide in your own handwriting |
| Complete hand-drawn diagram | To be drawn by students | Not Yet Verified | Draw in pen, do not print |
| Deadline | Assignment PDF states 20 Oct 2026, 8:30 AM | Not Yet Verified | Complete all submissions before deadline |

## Changes made in this revision
1. Relationship lines re-routed: none passes through a class box or crosses another line.
2. Composition diamonds are now drawn at the owner end (PurchaseOrder, Sale) as real line-end markers.
3. Multiplicities and relationship names placed beside the correct line end; subtitle no longer overlaps a class.
4. Added OrderStatus and SaleStatus enumerations (previously used as types but undefined).
5. Removed Supplier.createPurchaseOrder (duplicate); Employee.createPurchaseOrder now takes a Supplier.
6. Replaced Category.addProduct/removeProduct (redundant with the association) with updateDescription and getProductCount.
7. Report 2, README, specification and guides updated to match.

## Still your job
- Open the .drawio file in diagrams.net once and check it.
- GitHub upload and Google Form submission.
- Handwritten summary and hand-drawn diagram in pen.
