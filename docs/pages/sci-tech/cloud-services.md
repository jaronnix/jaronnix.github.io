Pathware is building a PACS-like (Picture Archive & Communication System) image storage solution so that it can offer digital slide management functionality to compliment the Bioptic imaging device. We are making the investment in developing this software based on the assumption that clinicians will be interested in viewing images created on Bioptic for verification and diagnostic purposes.

This proprietary image storage solution is advantageous in a number of ways. First, it minimizes the initial configuration overhead that comes with integrating with the existing PACS used by customer hospitals. Having our own cloud-based PACS built with web-services that are maintained and monitored by Pathware will likely provide a performance and reliability advantage that would be harder to achieve when interfacing with PACS systems not specifically tailored to the large images created by the Bioptic unit. There is also a significant strategic value in having a library of anonymized cytology slide images available to use to train machine learning models for future analytical or diagnostic products.

### **Architecture**

---

Our PACS is a Java SpringBoot Application that uses the AWS S3 key-value store to archive anonymized slide images and serves these images in compliance with DICOM standards.

### **Features**

---

- HIPAA Compliant
- EHR Integrated
- Web Viewer
- Anonymized storage
- AWS S3 key-value store => no database as part of architecture and no query-ability
- 

### **PACS Comparison**

---

The Pathware PACS integrates with the EHR and Hospital Network differently than a local PACS. Instead of working through a Database Gateway, the Bioptic unit communicates directly with the Pathware PACS through the hospital VPN and the clinician accesses the images through a request to the cloud-based image server instead of to a local PACS.

### **Future Features and Extensibility**

---

- Maintain PHI relevant to algorithms
- Become a VNA that can store images from other modalities to use for ML model training
- Implement query functionality
- Create a non-EHR implementation that allows access to web viewer w/o button

### **Development Status**

---

The basic functionality of creating DICOM files, storing them locally in the Spring app, and serving them to the web viewer application has been implemented. We need to finalize and implement a SSL certificate strategy that can be deployed as part of the EHR integration and we need to encrypt data at rest to achieve HIPAA compliance. We also need to deploy the application to AWS.

### Diagrams and Codebase

---

[Secure Box link](https://pathware.box.com/s/t3g6hfzzmkn6xe6szqsgnll3fz3rczil)