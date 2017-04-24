## Requirements

* fully automated user manual generation
* upgradability to a new auto-generated version (i.e. hold references to old fields/values and act accordingly - try to mimic their behavior according to their class/type/group)
* upgrade would also allow automatic (but optional) usage of old and new values (schemas) at the same time for a certain period (e.g. across multiple upgrades) maybe a possible solution: define a temporary BPMN graph
* continuous integration (i.e. real-time UI generation for presentation...)
* UI generation
* bindings to storage or even database (Camlistore/Tahoe-LAFS/Google/Amazon...)
* Information System Model and Architecture Generator
* interface modules for enterprise messaging systems/buses
* remote API
    * is versioned (version is being checked in each session/request)
    * incorporates detailed monitoring
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
* direct/lead the designer to update the model immediately from the bottom requests (people performing the processes), but not from top!
* support for multiple data/DB "backends" (useful e.g. for separating of confidential data from the other data)
* ability to work without central server/authority (=> explore P2P with regard to velocity due to real-time collaboration)
* support for running solely off-line (i.e. only locally or on LAN)
* security hardened outputs (preventing e.g. LD_PRELOAD etc. on all platforms including mobile ones)
* allows easy application of methods for automatical search for (sub)optimal input coefficient ranges, i.e. constraint optimization problems (e.g. simulated annealing)
* modeling tool and mainly generated binaries are clean for antivirus programs (ask for exception in Symantec, AVG, etc.?)
* The modeler shall support auto generation of processes based on a specification of the initial state (includes also all available resources) and the goal. Planning languages as PDDL [8] might be one of the ways to go. Generation should have 2 variants:
    * `one-shot`, which runs the generation only once and places the result to the defined place to be modified by a human
    * `continuous`, which runs generation automatically each time anything from the goal or initial state changed (e.g. available resources like roles or actual persons) and provides the result read-only (non-modifiable by anything)

## UI auto-generation

* constraint defined UI (including accessibility measures for visually impaired etc.)
* each collection/bigger_item could have an icon (derived from the name of the item or the content of the collection recursively)
* show tasks in parallel process branches next to each other (tiled, tabbed, ...)?
* a general way how to "jump" to predefined locations or e.g. "recently viewed" in GUI
* a general way how to handle non-standard situations (a need to "get back" to previous screen in GUI or previous step in the process etc.)
    * rule No. 1: all errors are **recoverable** (by humans)
* each "widget" remembers last used value on a per "widget" instance basis and offers this value along with the default value (**with the same importance** - preferably next to each other)
* web front-end design maybe in cooperation with
    * http://www.portadesign.cz/en/proc-nas-vybrat
    * http://www.arsyline.cz/
* combo-like "widgets" will scroll to the beginning (or end) if the currently selected item is only 3rd or less from the beginning (or end respectively)
* long-living "widgets" (e.g. apps, logos, headers, footers) in case they're used in two manual tasks in one process by the same role and no other role changed them in between
* each "widget" must support a "diff" feature (new + old value) to cope with real-time changes
* inspiration in W3.CSS design templates (W3.CSS is framework in pure CSS)

## Platforms

Assuming Redis will be used as storage (https://muut.com/blog/technology/redis-as-primary-datastore-wtf.html , http://oldblog.antirez.com/post/redis-persistence-demystified.html ). Make sure the underlying filesystem forces the HW standard (e.g. SATA) to use/flush write barriers, because it's often broken in HDDs and additionally filesystems do not enforce it.

Thorough guide how to scale Redis: http://petrohi.me/post/6323289515/scaling-redis .

FIXME propagation of "stored" info back to the requester

    * it seems each (**?**) "write" Redis command "returns" once the chosen persistence settings are satisfied (so if `fsync()` is set for each command in AOF, then it's fully durable maybe except for pipelining, when we can loose the last "group" of commits (but not the whole last 1s window))

FIXME high performance data flow

### Desktop:Windows 10

* https://github.com/MSOpenTech/redis
    * `fork()` implementation?

### Desktop:Mac OS X

### Desktop:Ubuntu

### Mobile:Android

* is it required to use JNI or can we embed C code more easily?
* `fork()` works, but might be a bit tricky with Java VM APPS (e.g. due to excess memory demands - use overcommit?); see also `posix_spawn()` (https://github.com/axiak/java_posix_spawn ) `vfork()` `clone()`
* use only generic widgets with auto-placement
* `embed redis java`

### Mobile:iOS

* `fork()` not available => prepare (imitate) copy on write pthread fork just with threads; see also `pthread_create()`
    * `fork()` implementation in Cygwin
    * `redis thread safe`
    * `embed redis c`
    * [redislite](https://redislite.readthedocs.io/en/latest/ ) (Python "embedded" Redis)
* allow sharding among threaded instances instead of among process instances

## Existing stuff

### Tools

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

### Languages

* http://en.wikipedia.org/wiki/Dataflow_programming (must be useful also for ad-hoc DB querying - e.g. using unix-utils-inspired functions)
* BPEL4WS (IBM + M$ + BEA); exe lang for BPMN
* WCSI (Sun)
* WSFL (IBM)
* XLANG (M$)
* WSDL (??)
* BPMN 2.0; covers control, data (very loosely), authorization, exception
* BPML (BPMI.org; deprecated)
* JBPM3
* XPDL
* BORM
* YAWL
* PNML (Woped tool)
* SEAM; covers data (so well as SQL) + processes (loosely)

## Misc

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
* Identity Management, Access Management, and Single Sign-On (SSO) system
    * GSI (Grid Security Infrastructure) shall be used after logging in
    * https://en.wikipedia.org/wiki/List_of_single_sign-on_implementations
    * [Auth0](https://github.com/auth0/lock ) (the core is not open-source; supports on-site deployment; major platforms supported)
    * Keycloak (Identity and Access Management for Modern Applications, Services and APIs, login service)
    * [JOSSO 2](http://www.atricore.org/confluence/display/JOSSO1/JOSSO2+Birds-eye+View)
    * Atlassian Crowd identity mgmt (free for open-source, non-profit and classrooms; is it also authentication/login service?)
    * 2-factor auth, but guaranteed different channels (i.e. not banking APP and auth SMS on the same mobile device; rather a HW or SW calculator with inputs...)
* efficient RPC/RMI and serialization format
    * with type information included: http://www.lua.inf.puc-rio.br/gsoc/ideas2014.html#dynserial
    * fastest in the world: [Cap'n Proto](https://capnproto.org/ )
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
* register intellectual property at [EUIPO](https://euipo.europa.eu/ohimportal/cs/home )
* auto submit hashes of releases to codehash.db to improve security

## References to papers...

1. a shift from the application development to the application integration (assembling vs. programming) (Dumas et al. 2005)
1. Process Aware Information Systems (PAIS): "software system that manages and executes operational processes involving people, applications, and/or information sources on the basis of process models" (Dumas et al. 2005)
1. *The early ancestors of PAIS are the office information systems namely BDL (Hammer, Howe, Kruskal, & Wladawsky, 1977), SCOOP (Zisman, 1977), POISE (Croft & Lefkowitz, 1984), Officetalk-Zero (Ellis & Nutt, 1980), whose purpose was to automate the office functions such as document editing or communication. There were two research approaches, one relying on a procedural prescription of the tasks using Petri nets (Zisman, 1977; Holt, 1985; Hammer et al., 1977) and another being data-centered and focusing on the office’s objects manipulation.* (Elena Epure et al. 2013)
1. WORKFLOW – BPM SYSTÉMY (Ing. Tomáš Novotný, 2009); http://www.fit.vutbr.cz/study/courses/TJD/public/
1. SEAM: A State-Entity-Activity-Model for a Well-Defined Workflow Development Methodology (A. Bajaj & S. Ram, 2005); http://nfp.collins.utulsa.edu/bajaja/MyInfo/
1. The view-based approach to dynamic inter-organizational workflow cooperation (Issam Chebbi, Schahram Dustdar and Samir Tata, 2006) - nice & short descriptions of the "process" languages
1. The Cassowary Linear Arithmetic Constraint Solving Algorithm: Interface and Implementation; http://www.cs.washington.edu/research/constraints/cassowary/cassowary-tr.pdf (JS, C++, Java, SmallTalk implementations: http://www.badros.com/greg/cassowary/js/quaddemo.html)
1. Jörg Hoffmann, Ingo Weber, Frank Michael Kraft. **SAP Speaks PDDL: Exploiting a Software-Engineering Model for Planning in Business Process Management.** In Journal of Artificial Intelligence Research 44 (2012) 587-632. July 2012

## Sales

* multiple service variants
    * the cheapest will not use diplomatic messages (and thus say straight why are things as they are as it will favour leaf workers over managers in terms of the mainstream perception)
        * e.g. if the customer decides to have just the default not-so-awesome looking UI, then it will appear in built-in FAQs as "your manager <name|role> bought just the cheap variant with bad UI"
        * this option to show honest (non-diplomatic) messages might be mitigated by increasing the price by 0.5*price_of_highly_customized_UI
* optional audit capabilities (who logged where and when and what approximately has been used)
* Function points
    * auto-generated to estimate usual cost and time
    * should we add time-estimates to significant places in the model? (in order to better understand the complexity/priority_for_users and designate the future problematic places)


## Community

* conferences
* meetups

## Testing (use-cases, advertisement, marketing)

* products/services of http://www.u-sluno.eu/
* http://www.abclinuxu.cz/blog/vsichni_mame_radi_brozkwe/2017/4/cost-benefit-analyza-libreoffice-vs-ms-ofice-ve-firme (contact the guy and ask if he would be willing to cooperate - they would get a totally free customized IS and we some real experience with tiny businesses)
* if user input is expected, warn before (unintentional) closing/... as it would cancel the transaction/process/...
* there might be a code for service/script tasks allowing running pure excel models converted to C using https://github.com/tamc/excel_to_code
* HL7 medical XML schema (implemented e.g. by Iguana)
* companies using XPMA will have significantly lower costs of external consultants, because these do not need to spend time with direct hands-on analysis in your company, but rather just immediately take a look at the models of your implemented processes and data (this allows absolutely exact evaluation of the external consultant's work and calculation of his price)
* (read-only) ability to "stop the time" (and also move it backwards and then forwards)
* model the products from https://www.rsa.com/
* health care, hospital, and medical systems (company TrapX from CZ evaluating security vulnerabilities, data leaking, and the black market regarding health care; https://www.veeva.com/ makes CRM etc.)
* web UI auto testing (e.g. for continuous improvement aka CI) http://pa11y.org/
* rewrite [DBT2](https://dev.mysql.com/downloads/benchmarks.html ) (MySQL Benchmark Tool simulating large OLTP warehouses)
* statistics gathered for everything (especially for time and quality measures for each task for each assigned person, not role!)
* processes executable in a "debugging/creative" mode, where the process can start with any task (temporary hidden start event before the task?) - this'll also allow ad-hoc usage of certain forms or tasks separately without the need to (possibly tediously) build and run a modified copy of the current process (=> the execution should be "separated" from the in-production processes and shouldn't affect the availability of the process engine for those in-production processes)
* near-user usability (*I'll easily create my very own process of every-morning mail check'n reply workflow*)
* all web services (FAPI, MioWeb, etc.) from David Kirš
* law advising companies to support their products (e.g. start-up contracts with contractors and taxing)
* Hyperion Financial Management integration (adopt the "cube" *standard dimensions*: scenario, year, period, view, entity, value, account, intercompany\_partner; and other dimensions: cost\_center, product, segments/markets, customers, countries/geography, exchange\_variance\_analysis, data\_source, roll\_forward\_schedules/movement, KPIs/ratios, headcount)
* Liferay and M$ SharePoint integration
* running a household (shopping, trips & planning, keep track of all official documents & agreements & contracts & schedules & ..., birthday & nameday notifications & preparations, medical checkups, etc.)
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
