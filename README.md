# XPMA (eXtensive Process Modelling and Automation)

*Exchange tedious work for computer force!*

A rough description of the idea follows. First you can read the structured variant (TL;DR) and then "THE LONG STORY" written in a marketing-like way.

## TL;DR (a structured description)

We aim to create a theoretical background with corresponding implementation for automation of processes and workflows. The rough idea is to take a high-level process description language (BPMN 2.0, WSFS, BPEL4WS, XPDL etc.), extend it if utterly needed (we'd like to create a theoretical background for reasoning "why it's not needed to extend the existing chosen language" with discussion of possible solutions for treatment of cases which can't be covered by the language) and from a descriptions in this language generate a fully working system performing the modeled tasks. The approach might be viewed also as a very much extended and tailored integration.

The automation is hidden in the approach itself - it pushes one to create model which when implemented does nearly everything and if it stumble upon an undecidable case, the user will be asked for choosing the right option or even solving the problem and then "clicking a proceed button" to continue in the process. This is a completely reversed approach than nowadays, when one does every single bit manually, but for certain small tasks uses some semi-automated solution (small scripts or tricky/unfriendly systems etc.).

reasons:
* too much routine computer work nearly everywhere (offices of all kind - from leaders/managers through all industry workers up to doctors in hospitals)
* very low number of specialists understand systems/programs (because they're created in hurry "just for this particular case" and are closed source) => unnecessary diversity (each one is purely individual and incompatible) => extreme amount of testing and support/help needed
* theory around modeling processes is either purely theoretical (i.e. models can only be used manually in reality, because the theory background is too small/constrained/insufficient) or requires too much human intervention (for connecting, arranging, verification etc.)

arguments:
* no existing tool nowadays (neither IBM BPM nor jBPM nor Bonita nor Bizagi suite does it - those are only UIs for fill-in forms, but they don't offer auto-generation of DB, easy upgrade of processes, deployment on different places/technologies, no other input/output - just web interface which is good only for forms and visualization, nothing advanced like custom programmed logic)
Actually, Bizagi is the only one closer to our idea, but it's still too little automated and has various constraints (UI, their own engine, connectors too specific but non-parametrizable and platform-dependent tools, getting bloated, etc.). In other words, Bizagi supports only a subset of business processes. Our idea, if realized, is usable also for non-business processes. By the way, Bizagi made a huge leap in 2014 - before, it wasn't even close to our idea.
* easy update and maintainability
* easy extending and exchange of backends and frontends
* easy connection to existing systems with "remote interfaces"
* no need for verification (ratio model:implementation is guaranteed to be 1:1 because of generation) - forget about Barbora Zimmerová, *Modelling and Formal Analysis of Component-Based Systems in View of Component Interaction*, dissertation, 2008
* easy to validate (model is simple and self-describing)
* easy to create the model as ordinary users intuitively understand processes (compared to data models, transactions, objects, routines and all other IT stuff)
* easy to monitor anything in the system
* easy to accurately estimate costs and risks of any part of the system
* there is an utter need for different levels of process abstraction (our idea is feasible for all levels including primary, supporting and organizational processes)
* Google currently very much promotes the "small scripts" approach with it's own "Google Apps Script". It's extremely limited, but it's growing popularity shows, that there is a huge number of people/groups which need automation of processes (the Google Apps Script is most often used with Google Docs for connecting all of them and also e.g. for producing animated charts).
* growing need for a *flipped approach* - people creating value have to be creative and tell what they want/need instead of just obeying commands and getting used to inappropriate IT tools and processes

technical remarks:
* continuous integration (a prototype is executed in background immediately after a small change in the model occurs and will guide the user what he did improperly or what is missing/unclear/undecidable)
* multiplatform (both the tool and the resulting system)
* auto-generation of "remote interfaces" (REST, RPC, message busses, etc.)
* much simpler than the existing systems (mentioned in "arguments")
* backend-agnostic and frontend-agnostic (there'll be modules offering these specifics)
* scalability - the resulting systems will not use "engine", but will be stand-alone distributed and parallelized applications
* built with soft real-time messaging (e.g. collaboration) in mind (in the models themself and in the resulting system as well)
* later on there could be added some auto-inferable parts of process improvement (might be based on Product-Based Workflow Design "PBWD" or knock-out best practice (Van der Aalst) which is based on existing statistical probability measurements)
* use of "remote interfaces" provided by other SaaS/PaaS systems in models allow tight and extremely quick integration which is also well measurable using inherent metrics

general examples:
* information systems (both small and huge ones); e.g. administrative tasks
* automation of routine tasks of programmers, personal assistants, analysts, leaders, etc.
* web pages (portals etc.)
* mobile applications (as they usually don't employ much logic but just juggle with data)
* rapid prototyping
* documentation

Expected time for development in one person (full-time): 2 years for a very basic version. 3 years more for advanced modules, pre-prepared processes, connectors etc.

## THE LONG STORY (a marketing description)

In the following lines, we're describing an idea for a thesis and/or future development and especially practical deployment.

The ultimate goal is to automate processes into as high degree as possible. From our experience from different companies (big and also small ones), we can divide processes into two groups. We could call the first "virtual processes" as they're not significant for valuable outcomes (they don't contribute to production of real products/services) and are very often in accordance with different standards (ISO, CMMI, ITIL, etc.) as they can use the same wording, because they're overly general (like the standards) and "tangible processes" which (in)directly contribute to a specific non-empty set of valuable outcomes/goals (products and/or services).

It will allow to ease administrative tasks, make everything which works with digital data work automatically, make the system sustainable, maintainable and continuously changing in time without data-loss and without increased effort.

example 1) As a manager of small group of programmers, I was supposed to write regular reports about different aspects of the project(s) like changes of all kinds, new threats, deadlines, planning, everything what happend in the last period, audits and a lot more other stuff. Majority of the source data for these reports is already present somewhere on my computer or in different databases or other places from which I can query them.

example 2) Easing everyday tasks for teachers at ground and high schools.

Both cases have two major things in common. The very last and most important result is something user-facing (document or visualization). Second, both are processes run repeatedly many times. And third, both need frequent changes (although not extremely big ones) in the process itself. Nowadays, if I ask any IT specialist for help, I'll get the answer "We'll do a super shiny information system especially tailored for you for tenths of thousands of dollars in 6 months with maintainance cost of 100 dollar/month with minor changes in the IS included". We ourself consider this ridiculous, because none od the two very common examples (actually, similar cases are the most common need in both giant companies and SMEs disregarding if they're IT or just some bricklayer, in home/personal accounting) were so much complicated, that one would need to employ bunch of guys, run a decent project for 6 months and deliver a super expensive product with expensive maintainance (whose cost will grow exponentially, because it's coded by humans). This also holds for huge infromation systems with many input interfaces and many output interfaces (imagine an enterprise messaging hub).

We noticed, that the problem specification using a conceptual model actually exactly meets the functional user requirements. We also came across one project for Czech Ministry of labour and social affairs where there was no time to make a friendly user-interface (the deadline was cca 4 months after the project started) and as such, the resulting system was actually 1:1 copy of the conceptual model. This system is successfully used nowadays and actually has a little bit steeper learning curve than other systems, but on the other hand, each change of the system doesn't brake the current user-interface almost in any way. Which means, that users don't need to change their behavior every month after deployment of new version as is quite common for usual information systems.

We want to address all the issues imposed by the current approach. This is the time of creation, ease of deployment, ease of change (for the maintainer, but also for users) and portability. According to our current technical specification of our system, the system for Ministry of labour and social affairs would be done (with testing) in few weeks (about 3), would be backend agnostic (wanna use your own DB server? or Amazon? or Google?; wanna use different infrastructre? your own? local provider? Google?; wanna use different authentication and authorization methods seamlessly? wanna have different outputs (PDF, email, web interface, QML interface, Android APP, electronic governmental tax system, whatever...)?; wanna be sure, that even if my company disappear/bankrupt, all the data, all the knowledge around the deployed system is still available?) and would have much lower risk of errors as most of the human labour would be eliminated.

Properties will include remote interface auto generation (with authentication, of course) and will employ an approach "everything automated with occasional human intervention" rather than the current "humans do everything with a small number of exceptions for specific semi-automated subtasks" - our goal is to avoid human labour. If this goal sounds weird, then look at the best nature-friendly economy models available. It's pleasant to realize, that if the mankind used all the currently existing technology used in production on proper places, each adult would need to work less than 2 hours per day in a workweek. Begin with The Zeitgeist Movement and resource-based economy model.

## Authors
* [Jan Pacner](https://www.linkedin.com/in/pacnerjan)
