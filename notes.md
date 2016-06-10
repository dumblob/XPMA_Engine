#### languages (http://en.wikipedia.org/wiki/Dataflow_programming)
* BPEL4WS (IBM + M$ + BEA); exe lang for BPMN
* WCSI (Sun)
* WSFL (IBM)
* XLANG (M$)
* WSDL (??)
* BPMN 2.0; covers control, data (loosely), authorization, exception
* BPML (BPMI.org; deprecated)
* JBPM3
* XPDL
* BORM
* YAWL
* PNML (Woped tool)
* SEAM; covers data + processes

#### requirements

* upgradability to a new auto-generated version (i.e. hold references to old fields/values and act accordingly - try to mimic their behavior according to their class/type/group)
* upgrade would also allow automatic (but optional) usage of old and new values (schemas) at the same time for a certain period (e.g. across multiple upgrades) maybe a possible solution: define a temporary BPMN graph
* continuous integration (i.e. real-time UI generation for presentation...)
* UI generation <-> constraint defined UI (including accessibility measures for visually impaired etc.)
    * web front-end maybe made by http://www.portadesign.cz/en/proc-nas-vybrat
* bindings to storage or even database (Camlistore/Tahoe-LAFS/Google/Amazon...)
* Information System Model and Architecture Generator
* interface modules for enterprise messaging systems/buses
* remote API has to be versioned and the version checked in each session/request
* Research and Implementation of Code Generator for Information System Based on SOA
* remote API technologies (protocols, existing wide-spread systems, ...)
    * Amazon Kinesis Modular Input
        * Index data from Amazon Kinesis, a fully managed service for real-time streaming data.
    * MQTT Modular Input
        * Index messages from MQTT, a machine-to-machine connectivity protocol, by subscribing Splunk software to MQTT Broker Topics.
    * SNMP Modular Input
        * Collect data by polling attributes and catching traps from devices providing cooling and power distribution in the datacenter.
    * Kafka Modular Input
        * Index messages from Apache Kafka messaging brokers, including clusters managed by Zookeeper.
    * REST API Modular Input
        * Poll local and remote REST APIs and index the responses.
    * JMS Modular Input
        * Poll and index data from messaging queues from providers such as TibcoEMS, Weblogic JMS and ActiveMQ.
    * AMQP Modular Input
        * Index data from message queues provided by AMQP brokers.
    * Splunk App for Stream
        * Capture, filter and index real-time streaming wire data and network events.
* On generators for embedded information systems
* An I-CASE system for automatic generation of MIS software-MISG/CASE
* a possibility to generate larger modules separately with secure remote interface and parallel execution of those to be able to scale and run in a distributed env
* a possibility to disable some parts/chosen_functionality on-the-fly/in_runtime (useful for maintenance etc.)
* auto-generated bindings for chosen identity/permission services (e.g. Google/F/twitter accounts)
* no support for auto-conversion for existing data from existing systems - this switch will always be done manually (e.g. by hand-written scripts) for very high price (due to great amount of manual labor and risk of mistakes/errors)!
* thorough simulation of the whole business possible
* adhoc (not affecting versin etc.) queries/changes_to_models allowed
* well-queriable DB of models (i.e. the models' syntax/format should be very strict and distinct) - e.g. "I want a model using this feature, this feature and providing this feature"
* a general way how to handle non-standard situations (a need to "get back" to previous screen in GUI or previous step in the process etc.)
* a general way how to "jump" to predefined locations or e.g. "recently viewed" in GUI
* direct/lead the designer to update the model immediately from the bottom requests (people performing the processes), but not from top!
* support for multiple data/DB "backends" (useful e.g. for separating of confidential data from the other data)
* ability to work without central server/authority (=> explore P2P with regard to velocity due to real-time collaboration)
* support for running solely off-line (i.e. only locally or on LAN)

#### existing tools
* http://www.workflowpatterns.com/vendors/
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
* GeneXus Evolution 3 and GeneXus Business Process Management Suite (http://www.genexus.com/products/business-process-management-suite?en ) - quite nice and comprehensive IS generators with native and Web outputs for M$ Windows, Android and BlackBerry
* WaveMaker - open source web RAD with semi-auto GUI generation (http://www.jguru.com/article/tools/wavemaker-brings-rad-to-the-cloud-with-one-click-deployment.html )

#### function points auto-generated from the BPML/... to estimate usual cost
* should we add time-estimates to significant places in the model? (in order to better understand the complexity/priority_for_users and designate the future problematic places)

#### misc
* backend DB
    * [Mnesia](http://erlang.org/doc/man/mnesia.html ) - a distributed telecommunications DBMS (leverages Erlang)
    * [Datomic](http://www.datomic.com/) - the fully transactional, cloud-ready, distributed database (leverages Datalog)
* manage virtual machines in the Google Compute Engine (https://github.com/GoogleCloudPlatform/kubernetes)
* curses CLI front-end howto http://ccfe.altervista.org/
* From the analysis of the primary studies extracted, it can be concluded that the improvement approaches can be generated at an organizational or a technical level. It should be emphasized that there are studies (11%) which, in the quest to support actions of process improvement, propose the supplying of technical tools and facilities that support the activities related to the processes. This is termed as technical infrastructure and includes features such as document templates, process models, techniques and tools.
* see Pino et al. 2008
* syntax for the graph (http://blog.duangle.com/2015/01/conspire-programming-environment-for.html?m=1)
* NoFlo (syntax for the graph): http://noflojs.org/documentation/fbp/
* enterprise architecture design (~ the top of the business process architecture); Remco Dijkman, Irene Vanderfeesten, Hajo A Reijers, *The road to a business process architecture: an overview of approaches and their use*, 2011
* Keycloak (Identity and Access Management for Modern Applications, Services and APIs, login service)
* [JOSSO 2](http://www.atricore.org/confluence/display/JOSSO1/JOSSO2+Birds-eye+View) Identity Management, Access Management and Single Sign-On system
* Atlassian Crowd identity mgmt (free for open-source, non-profit and classrooms; is it also authentication/login service?)
* efficient RPC/RMI and serialization format with type information included (http://www.lua.inf.puc-rio.br/gsoc/ideas2014.html#dynserial)
* look at the following keywords/facts
    * BPSim (WfMC standard)
    * decision tables (maybe equivalent to "table rules")
    * business rules
    * BAM
    * "HA runtime data" is very important for managers/business
    * jBPM rules
        * Java (native lang)
        * DSL (from natural lang)
        * table rules
        * guided rules (a form with ...)
    * jBPM has 20 ms overhead

#### references to papers...
* a shift from the application development to the application integration (assembling vs. programming) (Dumas et al. 2005)
* Process Aware Information Systems (PAIS): "software system that manages and executes operational processes involving people, applications, and/or information sources on the basis of process models" (Dumas et al. 2005)
* *The early ancestors of PAIS are the office information systems namely BDL (Hammer, Howe, Kruskal, & Wladawsky, 1977), SCOOP (Zisman, 1977), POISE (Croft & Lefkowitz, 1984), Officetalk-Zero (Ellis & Nutt, 1980), whose purpose was to automate the office functions such as document editing or communication. There were two research approaches, one relying on a procedural prescription of the tasks using Petri nets (Zisman, 1977; Holt, 1985; Hammer et al., 1977) and another being data-centered and focusing on the office’s objects manipulation.* (Elena Epure et al. 2013)
* WORKFLOW – BPM SYSTÉMY (Ing. Tomáš Novotný, 2009); http://www.fit.vutbr.cz/study/courses/TJD/public/
* SEAM: A State-Entity-Activity-Model for a Well-Defined Workflow Development Methodology (A. Bajaj & S. Ram, 2005); http://nfp.collins.utulsa.edu/bajaja/MyInfo/
* The view-based approach to dynamic inter-organizational workflow cooperation (Issam Chebbi, Schahram Dustdar and Samir Tata, 2006) - nice & short descriptions of the "process" languages
* The Cassowary Linear Arithmetic Constraint Solving Algorithm: Interface and Implementation; http://www.cs.washington.edu/research/constraints/cassowary/cassowary-tr.pdf (JS, C++, Java, SmallTalk implementations: http://www.badros.com/greg/cassowary/js/quaddemo.html)

#### testing (use-cases, advertisement)
* statistics gathered for everything (especially for time and quality measures for each task for each assigned person, not role!)
* processes executable in a "debugging/creative" mode, where the process can start with any task (temporary hidden start event before the task?) - this'll also allow ad-hoc usage of certain forms or tasks separately without the need to (possibly tediously) build and run a modified copy of the current process (=> the execution should be "separated" from the in-production processes and shouldn't affect the availability of the process engine for those in-production processes)
* near-user usability (*I'll easily create my very own process of every-morning mail check'n reply workflow*)
* Hyperion Financial Management integration (adopt the "cube" *standard dimensions*: scenario, year, period, view, entity, value, account, intercompany\_partner; and other dimensions: cost\_center, product, segments/markets, customers, countries/geography, exchange\_variance\_analysis, data\_source, roll\_forward\_schedules/movement, KPIs/ratios, headcount)
* Liferay and M$ SharePoint integration
* **Domov pro mne**

    Domov pro mne poskytuje osobní asistenci dětem i dospělým se zdravotním postižením. Tuto službu vykonávají zaměstnanci v domácnosti uživatelů služby nebo v jiném prostředí dle potřeby (např. škola, zaměstnání). Dále Domov pro mne organizuje řadu zážitkových pobytů a společenských akcí pro osoby s handicapem.

    Zadání:

    Proveďte analýzu stávajícího systému tvorby časového harmonogramu sociální služby osobní asistence a na to navazující agendy pracovní docházky, fakturace za služby a vykazování statistických dat. Vytvořte návrh funkčnosti systému a implementujte. V co největší míře využijte technologie a informace, které jsou již k dispozici v rámci organizace.

    Nový systém bude schopen:

    * párovat uživatele osobní asistence a pracovníky (osobní asistenty) organizace do časového rozvrhu
    * generovat časový rozvrh specifický pro uživatele a specifický pro pracovníka
    * vytvářet přehled čerpání asistenčních hodin a vytíženosti jednotlivých pracovníků
    * vytvářet podklady pro fakturaci za poskytnutou službu osobní asistence
    * vytvářet podklady pro interní účetnictví a platby zaměstnanců

    V současné době organizace využívá Google Apps pro správu zaměstnanců a správu interních dokumentů.
* PRINCE2 document generators (forms, graph drawing, export; Harward Business Reviews subscription)
* IS generator
* info about the work of salesmens, state and development of the communication with customers, state of the offerings and trading/sales cases, notes from meetings/negotiations/deals, payment policy and it's obedience, etc.
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
