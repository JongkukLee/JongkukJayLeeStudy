---
layout: default
---
---
# Component Based Development (CBD)
---
Today the main concern in enterprises business system is in reducing its development and maintenance cost of managing complexity system, frequently changed the business process, and the risk of developing the new system. [Component Based Development (CBD)](http://) is rising as the excellent solution to solving such problems. CBD is a methodology of software engineering that is able to enhance the **independence, reusability, and parallel work** through design components from the beginning phase of the project. (Stojanovic, Dahanayake)<br />

In modern object-oriented, a [component](http://) is a "reusable program building block", which not only can be used as independent functionality and but also easily can be combined with other components using interfaces.<br />

Moreover, component-oriented technologies focus on the distribution of the **reusable components** in networks using the infrastructure of the Internet.<br />

VBX controls, DCOM/COM, CORBA and Java Beans, COM+/.NET, and Enterprise Java Beans (EJB) are now widely used as the solutions for the component based projects in a distributed network environment.<br />

This website does not cover all CBD concepts or component technologies.<br />

This website concentrates on the introducing how to develop the components with some programming frameworks such as **Java frameworks (MVC, Spring, ADF) or Javascript frameworks (NodeJS, React, and Angular)**.<br />

All samples are illustrated the study cases based on my experiences via participating in the development of [POSCO](http://) [MES](http://) system and in the maintenance team.<br />

I hope all visitors can share the concepts and skills here with me and all advice and wrong information that is found will be pleased for me.<br />

If you would like to move to the next stage, please click the [UI-Component](/CBDProject/contents/uicomponent) or [NON-UI Component](/CBDProject/contents/nonuicomponent) menu.<br />

Thank you for all your interests.<br />

Jongkuk Lee.<br />

## POSCO MES ##

>[POSCO]() is the the world's fourth-largest steelmaker by this measure in 2015. As steel-making is the most process industory, there is pursuited non-stop system from plan to delivery.<br />
![Image]({{ site.globalurl }}/contents/img/posco.jpg)

>[MES (Manufacturing Execution System)]() is the management system of the produce activity management system on real-time from determining the optimized job-order to garunteeing the quality assurance.
There was POSCO project Between 2002 and 2004 with nearly 300 million dolar IT buget.<br />

## KEY TERMS ##
**Architecture:** The fundamental organization of a system, embodied in its components, their relationships to each other and the environment, and the principles governing its design and evolution (ANSI/IEEE Standard 1471-2000).
**Architecture Viewpoint:** An abstraction of a set of concerns on a system derived by using a set of concepts and rules of structure (RM-ODP).<br />
**Component:** An encapsulated, autonomous, service-based software unit that delivers useful services through the well-specified interface to its environment.<br />
**Component-Based Development:** A software development approach where all aspects and phases of the development lifecycle are based on components.<br />
**Component Interface:** The behavior of a component along with constraints at a subset of component’s interactions, data types used in exposing the behavior, configuration and quality parameters of the behavior.<br />
**Component Middleware:** A commercially available component technology and its associated connectivity capabilities; includes, for example, CORBA components, EJB and COM+/.NET.<br />
**Model:** Represents the system from a set of concerns. A model can be informal, semi-formal and formal. A system is typically represented by a set of models, each addressing some particular area of concern.<br />

## Reference: ##
>Stojanovic, Zoran, and Ajantha Dahanayake. "Component-Oriented Approach for Designing Enterprise Architecture." Encyclopedia of Information Science and Technology, edited by Mehdi Khosrow-Pour, vol. 1, Idea Group Reference, 2005, pp. 481-487. Gale Virtual Reference Library, go.galegroup.com.libaccess.senecacollege.ca/ps/i.do?p=GVRL&sw=w&u=king56371&v=2.1&it=r&id=GALE%7CCX3466500095&sid=exlibris&asid=c75ea1b71c597ba5b82d4680b56296e2. Accessed 27 Oct. 2017.