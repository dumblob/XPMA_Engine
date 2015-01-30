#### languages (http://en.wikipedia.org/wiki/Dataflow_programming)
* BPEL4WS (IBM + M$ + BEA); exe lang for BPMN
* WCSI (Sun)
* WSFL (IBM)
* XLANG (M$)
* WSDL (???)
* BPMN 2.0; covers control, data (loosely), authorization, exception
* BPML (BPMI.org; deprecated)
* JBPM3
* XPDL
* BORM
* YAWL
* PNML (Woped tool)

#### requirements
* upgradability to a new auto-generated version (i.e. hold references to old fields/values and act accordingly - try to mimic their behavior according to their class/type/group)
* upgrade would also allow automatic (but optional) usage of old and new values (schemas) at the same time for a certain period (e.g. across multiple upgrades) maybe a possible solution: define a temporary BPMN graph
* continuous integration (i.e. real-time UI generation for presentation...)
* bindings to storage or even database (Camlistore/Tahoe-LAFS/Google/Amazon...)
* Information System Model and Architecture Generator
* Research and Implementation of Code Generator for Information System Based on SOA
* interface modules for enterprise messaging systems/buses
* On generators for embedded information systems
* An I-CASE system for automatic generation of MIS software-MISG/CASE
* a possibility to generate larger modules separately with secure remote interface and parallel execution of those to be able to scale and run in a distributed env
* a possibility to disable some parts/chosen_functionality on-the-fly/in_runtime (useful for maintenance etc.)
* auto-generated bindings for chosen identity/permission services (e.g. Google/F/twitter accounts)
* remote API has to be versioned and the version checked in each session/request
* no support for auto-conversion for existing data from existing systems - this switch will always be done manually (e.g. by hand-written scripts) for very high price (due to great amount of manual labor and risk of mistakes/errors)!
* thorough simulation of the whole business possible
* adhoc (not affecting versin etc.) queries/changes_to_models allowed
* well-queriable DB of models (i.e. the models' syntax/format should be very strict and distinct) - e.g. "I want a model using this feature, this feature and providing this feature"
* a general way how to handle non-standard situations (a need to "get back" to previous screen in GUI or previous step in the process etc.)
* direct/lead the designer to update the model immediately from the bottom requests (people performing the processes), but not from top!
* support for multiple data/DB "backends" (useful e.g. for separating of confidential data from the other data)

#### existing tools
* WebRation software comprises nearly everything needed:
  * BPMN/BPEL BPML
  * support for EDI (http://en.wikipedia.org/wiki/Electronic_data_interchange)
  * IFML (= successor of WebML)
  * how to combine BPM and WebML (http://www.webml.org/webml/page87.do?UserCtxParam=0&GroupCtxParam=0&ctx1=EN)
* BonitaBPM
  * BPMN 2.0, JBPM3 XPDL
* Gliffy - web drawing different diagrams (including BPMN) & UI mock design
* Archi - comprehend, but too demanding BPMN modeller in Java
* Enterprise Architect
  * http://www.sparxsystems.com.au/products/ea/index.html
* OpenCASE and BORM

#### function points auto-generated from the BPML/... to estimate usual cost
* should we add time-estimates to significant places in the model? (in order to better understand the complexity/priority_for_users and designate the future problematic places)

#### misc
* manage virtual machines in the Google Compute Engine (https://github.com/GoogleCloudPlatform/kubernetes)
* curses CLI front-end howto http://ccfe.altervista.org/
* From the analysis of the primary studies extracted, it can be concluded that the improvement approaches can be generated at an organizational or a technical level. It should be emphasized that there are studies (11%) which, in the quest to support actions of process improvement, propose the supplying of technical tools and facilities that support the activities related to the processes. This is termed as technical infrastructure and includes features such as document templates, process models, techniques and tools.
* see Pino et al. 2008
* syntax for the graph (http://blog.duangle.com/2015/01/conspire-programming-environment-for.html?m=1)

#### references to papers...
* a shift from the application development to the application integration (assembling vs. programming) (Dumas et al. 2005)
* Process Aware Information Systems (PAIS): "software system that manages and executes operational processes involving people, applications, and/or information sources on the basis of process models" (Dumas et al. 2005)
* *The early ancestors of PAIS are the office information systems namely BDL (Hammer, Howe, Kruskal, & Wladawsky, 1977), SCOOP (Zisman, 1977), POISE (Croft & Lefkowitz, 1984), Officetalk-Zero (Ellis & Nutt, 1980), whose purpose was to automate the office functions such as document editing or communication. There were two research approaches, one relying on a procedural prescription of the tasks using Petri nets (Zisman, 1977; Holt, 1985; Hammer et al., 1977) and another being data-centered and focusing on the office’s objects manipulation.* (Elena Epure et al. 2013)
* WORKFLOW – BPM SYSTÉMY (Ing. Tomáš Novotný, 2009); http://www.fit.vutbr.cz/study/courses/TJD/public/

#### testing (use-cases, advertisement)
* near-user usability (*I'll easily create my very own process of every-morning mail check'n reply workflow*)
* IS generator
* generator for RPM spec files
* automated configuration mgmt (http://sharknet.us/2014/02/01/automated-configuration-management-challenges-with-idempotency/)
* VENTUS® Software (ERP systém pro komplexní řešení procesů v obchodních a obchodně-výrobních společnostech s výraznou podporou řízeného skladu - WMS.)
* myAVIS™ Mobile Solutions (Řešení pro efektivní a kvalitní řízení v oblasti obchodních, servisních, marketingových, výrobních a distribučních činností v terénu.)
* myFABER™ Service Management (Řešení pro efektivní řízení procesů, provozu a služeb v energetice, utilitních a servisních společnostech s podporou pracovníků v terénu.)
* myWORK™ Work Management (Řešení pro efektivní a kvalitní řízení lidských zdrojů, s důrazem na skupinu středního managementu, takzvaných „white collar pracovníků“.)
* mySTOCK™ Warehouse Management (Řešení efektivního a komplexního řízení logistiky, optimalizace skladovacích procesů s plnou podporou mobilních zařízení a pracovníků.)
* myTEAM™ Workflow Management (Řešení optimálního oběhu a správy dokumentů, sdílení a využívání informací pro snadnou a efektivní spolupráci týmů i jejich členů.)
* myMACHINE™ Work Management (Řešení kontroly a řízení efektivity výroby, identifikace a odstranění prostojů, ztrát a kritických míst všech výrobních procesů.)
* myCASH™ Retail Management (Řešení maloobchodního prodeje s rozsáhlými funkcemi pro jednotlivé prodejny i pro řízení rozsáhlých sítí a obchodních řetězců.)
* myDATACENTER™ Data Solutions (Řešení spolehlivého a maximálně bezpečného provozu aplikací, dat a projektů s vysokou garantovanou dostupností a kvalitou služeb.)
