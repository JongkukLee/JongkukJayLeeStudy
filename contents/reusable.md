---
layout: default
---
---
# Reusable Component
---

When mentioning [Compnent Based Development (CBD)](http://), we need to focus on one keyword ['Reusable Components'](http://), which are modules independently run the funtionalities in software system but can be applied in mulitple applications. Assuming a software as a hardware, CPUs, memory cards, and LAN cards provide  easy replaceability to upgrad or fix the parts. Like hardware parts, in CBD projects, reusable components gives high replaceability of software parts and provides better solution to approach the complexity of system.<br />

When a project starts, components should be classified in the view of reusability and be checked the adaptibility through developping and applying the prototypes. In the next phase, it should be defined and analyzed in the business and system perspective for developping the components. In the stage of implementation, such deliverables will be more clearly designed and implemented as components.<br />
#### Figure1.how to apply reusable components in applications ####
![Image]({{ site.globalurl }}/contents/img/reuse1.jpg)

Figure1 shows the developing procedure and the usage for reusable components. The components are managed in the component pool. Developers can select and apply the components, which are needed in their user interface (UI) applications or non user interface (NON-UI) applications. Note that there are all UI components, NON-UI components and common ones in one component pool.<br />

#### Figure2.when components change ####
![Image]({{ site.globalurl }}/contents/img/reuse2.jpg)

Figure2 shows when the components are changed, there are little effects in the applications. That is the most reason of why we use  reusable components in projects.<br />

#### Figure3.Reusable Components Deploy ####
![Image]({{ site.globalurl }}/contents/img/reuse3.jpg)

Figure3 shows where components are located in MVC -- **Model, View, Controller** -- model. In **View** part, the components have functionalities to display a logo, list of views (Lovs), tables, scrolls and so on using JAVA script, Tag Library, Applet. In **Controller part**, the components play a role in controllinga and processing the request from processing computers (P/C), enterprise resource planning (ERP) system, and other external systems. Also, this layer can controll and transact the data from graphic user interfaces (GUIs). Lastly, in **Model** layer, the components include the modules to connect to database system and to handle business rules. <br />

We can meet how to create web page using components in [UI Component]() part of this website, and [NON-UI Component]() menu introduces the control of requests, message communication, and the connection of database.