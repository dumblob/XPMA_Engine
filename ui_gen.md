# Vision

Take automatically discovered and then manually refined as input for https://algorithms.design/ (UI auto generation).

# UI

- user feedback (especially refusal) to GA-generated results shall be added as new fact for retraining of the neural network - this new fact would score very low (maybe directly zero because there shouldn't be any local min/max problem in here) in all properties
- https://interactionmining.org/rico - huge database for our genetic algorithm and neural network (maybe even some properties characterized by humans)
- https://www.floydhub.com/ - for developers developing the genetic algorithm and the neural network (see e.g. https://blog.floydhub.com/turning-design-mockups-into-code-with-deep-learning/ )
- https://ukit.group/en - fully automated UI generation from an existing UI/content (it's not working well as of 2021-03-08, but keep an eye on it as it's almost exactly what we're doing here)
- https://webscore.ai/ - maybe use instead of human feedback scoring?
- http://www.dgp.toronto.edu/~donovan/design/index.html - fully automatic layouting!
- https://bdickason.com/posts/speed-is-the-killer-feature/ (UI has to have NO latency at all cost!)
- vracet se v procesu kvuli korekci vstupu?
    - nejaky (pro kazdy task tagem nastavitelny?) timeout jako ma Gmail, kdy se akce jeste neprovede, i kdyz UI ukazuje, ze jiz ano
- most used tools by UX/UI designers
    - see comprehensive curated list https://github.com/ComponentDriven/componentdriven.org/blob/master/src/design-tools.ts
    - Sketch – 23%
    - Figma – 19%
    - Abstract – 10%
    - Storybook – 5%
    - Craft – 4%
    - pencil (on GitHub) - not part of the research; open source => candidate for the manual refinement of AI (genetic algo.) -generated UIs
- design & development & low-code & no-code tools:
    - https://www.invisionapp.com/studio (like Figma)
    - https://www.invisionapp.com/cloud/prototype (- || - but without advanced animations)
    - https://www.plasmic.app/
    - https://www.createwithplay.com/ (like Jasonelle)
- testing examples for advanced UI generation
    - https://www.gameuidatabase.com/?ref=screenlane
- inspiration by https://www.kodular.io
- Framer (a bit like Figma but with possibility to create native React components easily) https://uxdesign.cc/framer-is-still-alive-and-well-and-its-a-game-changer-43c8a4c6bd0
- UI animation, UI web design, etc. universal tool: https://www.creatopy.com/
- train the neural network with publicly available flows from https://overflow.io/
- list of existing complex picture visualizations (PNGs, JPGs, ...) of advanced & difficult to explain ideas
    - https://github.com/conceptviz/conceptviz.github.io/tree/master/img

## TODO

- TUI/CLI UI (much) better API than (n)curses - worth taking inspiration: https://github.com/mabe02/lanterna/tree/master/src/main/java/com/googlecode/lanterna/gui2
- use https://github.com/Claus1/unigui as inspiration for the simplest possible autolayout
- pre-fetch (cache) some data on mouse over
- repositories with fast neural networks (NN) etc.: https://github.com/lucidrains?tab=repositories
- a good simple example of genetic algorithm + neural network (not tree-based neural network though) is on https://github.com/ssusnic/Machine-Learning-Flappy-Bird
- instead of training own network, use OpenAI (at least GPT-3) as it can spit out very accurate results even if only very low number of examples were given
- https://www.researchgate.net/publication/3595236_Dynamic_hierarchical_self-organizing_neural_networks
- https://en.wikipedia.org/wiki/Lasso_(statistics)
- google: interative animation tool
    - object collisions (hard stop, bounce, physics, artificial, ...; ) aka object interaction and object synchronization; object transition (tweening/inbetweening, morphing, transformations, ...- see e.g. Synfig vector tweening); user-guided object collision/interaction/synchronization
    - bouncing/touching/interaction_with_other_objects (physics not needed, but just binary can collide/stop or can overlap)
    - tweening between different object instances
    - user interaction of final animation (actions/events - not just timeline, but user mouse/keyboard/..., existing object bouncing/touching, ..)
        - (it could be seen as yet another object - e.g. mouse pointer could be a mathematical point but with some mass)
    - recording of interaction during animation making
    - layouting, alignment/snapping to grid/borders_of_existing_objects, ...
    - hierarchical animation (e.g. a hamburger menu) versus flat animation (everything is just a predefined frame, i.e. it's non-interactive video)
    - combining/composing animations (e.g. imagine two connected BPMN tasks and you want to suddenly show a third task which was hidden and which shall replace the connection between the two already shown tasks => animate move of both existing tasks away from each other and at the same time animate "grow from tiny point" the new task and also animate the disappearance of the existing connection line)
        - the JS lib for animated data presentation
    - https://visme.co/blog/animation-software/
    - https://atomisystems.com/html5-animation/top-5-easy-to-use-web-animation-tools-that-bring-your-website-to-life/
    - https://yalantis.com/blog/web-animation-technologies-and-tools/
- for long/big UI pages/bpmn_tasks do NOT split them into separate smaller tasks, but rather generate UI in a way, that it first loads first smaller part/chunk and then automatically (or manually) loads the next part/chunk under the first part
    - could be logically split (e.g. question + answer; then automated/manual load, ...)
- inspiration which interactions, widgetss, animations, transitions, etc. exist
    - https://origami.design/
    - https://headlessui.dev/?ref=screenlane
- how to maintain UI similarity in case one is logged in and logged out (while accessing maybe 90% of data)? imagine github pull request when logged in and logged out (when logged in one can additionally comment and has just few icons in addition to unlogged state)
- naming convention
    - widget X element X ...
- add canvas-like UI features e.g. for live SCADA system view (i.e. top-down 2D view of a real warehouse with many differently shaped rooms, packages, etc.)
    - standard UI widgets could be "special cases" of such canvas objects, but with the "content" bitmap computed by the system which SCADA is running on?
    - take a look at view implementation in Red (open source REBOL successor)
    - this affects the "init" stage of GA
- constraints/dimensions/placing inspired by
    - [Figma constraints](https://www.youtube.com/watch?v=rRQAQ1d9q9w )
    - [ORCSolver: An Efficient Solver for Adaptive GUI Layout with OR-Constraints](https://github.com/YueJiang-nj/ORCSolver-CHI2020/blob/master/Code/ORCSolver%20(Ours)/video_example.py )
- layout inspiration from [Figma layout](https://www.youtube.com/watch?v=NrKX46DzkGQ )
- add 2 types of constraints
    - how shall certain (widget) settings look like (this will be "forced", i.e. simply overwrite the generated settings, before the "cleaning rules" phase starts)
    - how must certain (widget) settings not look like (this will get evaluated in the fitness function before the genetic algorithm starts)
    - maybe use ranges and not exact matching values?
    - ability co generate these constraints from an existing configuration to ease their addition/removal
- pridat "hierarchicnost" (ke kazdemu "slotu" neuronky?)
- globalni promenne ukazujici miru:
    - stromovost (mnozstvi krat sila/mira)
    - kolekcni opakovatelnost
    - zanoritelnost (mnozstvi_mist_se_zanorenimi krat hloubka_zanoreni)
- "weighting" (e.g. some users are more experienced than others)
    - http://proceedings.mlr.press/v97/konstantinov19a/konstantinov19a.pdf (https://blog.acolyer.org/2019/08/19/robust-learning-from-untrusted-sources/ )
- cleaning heuristics
    - distribution of fonts among all text element instances (one "widget" can contain zero to many such instances) in UI:
        - font1 everywhere except for 20% of places on the page having a different one out of which is font2 everywhere except for 20% of the given page percentage having a different one out of which is font3 everywhere except for 20% ... until the percentage accounts for just 1 element
    - distribution of non-text element heights and widths similarly constrained
        - shall be influenced by content type
    - the distribution weights will be tuned by the genetic algorithm
    - new dialog must never cover an existing one; successive dialogs should either be coalesced or with some artificial delay between and/or should be visually significantly (randomly?) set apart (e.g. color tint, misplaced/moved/shifted, ...) otherwise one could click a wrong button
    - does this hold only for fixed-size elements? how about "dynamic" (shrinkable/expandable) elements? maybe this could change some of those dynamic elements into fixed size elements (e.g. those being near other fixed elements or those having small content if any or just the first in a list sorted by the guessed importance/size/impact or just those having very similar sizes to many other elements to "unify" them)
    - see research how to introduce partial ordering in chaos

>haskman https://news.ycombinator.com/item?id=19745404
>I wrote a UI framework called Concur which is very similar to immediate mode UIs and hence very easy to use, but also scales fantastically well to complex UIs. The original code was written in Haskell (https://github.com/ajnsit/concur), and then ported to Purescript (https://github.com/ajnsit/purescript-concur), and even Javascript (https://github.com/ajnsit/concur-js).
>There's an introduction/tutorial here - https://github.com/ajnsit/concur-documentation/blob/master/R...
>
>jhpriestley https://news.ycombinator.com/item?id=19749029
>It looks like we've discovered the same approach in parallel. I even wrote a haskell version first, https://github.com/jhp/sneathlane-haste and then a js version using generators https://github.com/jhp/imperative
>Sneathlane is a little different because it outputs to canvas and has a rather complex Widget type to handle focus and to allow different outputs to work together, but the Monad instance has the same behavior of waiting for widget completion. Imperative leans more on the DOM, it has its own VDOM implementation where yours looks to use React's but otherwise the libraries look very similar.
>I'm a web developer, I've worked with everything from FRP to React, I think this approach is the best. I hope Concur will help to popularize it! I'm writing this on my commute but will be looking into this further today, to see if there's anything in Imperative that might enrich Concur or vice versa.

## Novel fast layouting algorithm in 2D suitable for automated UI generation

- endlessly shrinking & stretching mini live window with scroll support for every layout type (smartphone, tablet, desktop)
- "same" widgets found across different tasks have in GA priority as follows:
    1. the highest priority have widgets present in most tasks
    2. down to the lowest priority of widgets present only on 2 tasks
- sum of all widths/heights in a chain (a chain is one full path from root to a leaf in a tree) must be >= of the given platform (smartphone, tablet...)
- z-index
- dist. rel. "proportional" applies in the end also to growing/shrinking widgets in runtime
- growing/shrinking widgets must have at least one bbox (bounding box) axis with dist. rel. "fixed" (this allows runtime
- each bbox side has distance relation with one and only one (FIXME might have more in a tree?) bbox of another widget - 2 types of dist. rel.: fixed with number OR proportional
- each bbox axis (either of the 2 sides) is part of at least one chain of constraints which has at least one proportional dist. rel.
- default strategy is to fill as much space as possible (if overlapping enabled, it's considered lower priority)

## Genetic algorithm (GA) or similar (Ant Colony, ...) with neural network as fitness function

FIXME maybe use CPPN (compositional pattern-producing network) instead of GA (with fourier-features it's able to capture all details)?
    https://github.com/noahtren/Fourier-Feature-Networks-TensorFlow-2

See "GA and ACO in hybrid approach for Analog Circuit Performance Optimization (Benhala, Ahaitouf)", "A Puzzle-Based Genetic Algorithm with Block Mining and Recombination Heuristic for the Traveling Salesman Problem (Pei-Chann Chang, Wei-Hsiu Huang, Zhen-Zhen Zhang)", etc.

- pipeline
    - init
        - decision whether the surface with widgets will have **fixed height** (implies overlapping) or **variable height** with guaranteed no overlapping/hiding
            - make this specific for each of desktop, tablet, smartphone?
            - **fixed height** not necessarily implies that the height will be equal to the viewport height - GA will optimize the ratio between "height/length" of the scroll view and the overlapping depth
                - can generate partial overlaps (e.g. context help, more detailed information, etc.)
                    - heuristic: if only partial overlap, then try to prefer narrow column-like widget positioning first (like on a smartphone) instead of horizontal line-oriented widget positioning
                - depends on screen side ratios (for fixed height, we'll optimize for the most common ratio - currently 16:9 - and for smaller/bigger heights linearly scale the vertical space between widgets, not widgets themself (!), and in case it won't fit - i.e. is still too large - then start scrolling)
                    - rotated displays (e.g. 9:16) will also have their layout
                    - consider splitting wide ratios into several columns?
        - heristics to define optimal width and height of each widget (just PARTIAL subject to GA - e.g. here defined padding might cause impossibility to construct a layout having good results in the neural network fitness func)
            - similar widgets (e.g. more or less of the same type) will have the same height except for few...
                - this depends also on the end-user platform
        - heuristics to determine default significance of widgets (subject to GA)
        - follow hints from XPM tags regarding e.g. same-width info about several widgets, alignment info about several widgets, etc.
    - GA (crossover & mutation)
    - GA layout & design finishing routines (taking parts of GA results as arguments)
        - e.g. when two widgets have to have the very same width or being on the same "line" - i.e. having the same top bbox side relation to viewport
            - it would take immensely long for GA to determine that, so we'll just let GA determine the width (or relation distance aka "reldist" in the second example) and this stage will ensure assignment of this width (or reldist) to the two widgets
    - cleaning stage routines (what can't exist etc.)
        - in theory this stage is more or less superfluous as GA shall converge to correct/acceptable results, but it's faster to do it this way if we can than wait for GA
        - remove bits designating overlapping in case non-overlapping generation was requested or the target platform doesn't support overlapping
        - some regular alignment is preferred (humans feel, that grids are nice to look at)
        - crossing reldists in the same axis of a bbox are not allowed
        - UI "sins": https://dev.to/perborgen/learn-basic-ui-design-in-5-minutes-1mlk
    - fitness function
        - first some analytical checking routines
            - e.g. all text fits into labels for all known inputs (e.g. languages with supported fonts and their sizes and settings)
        - then neural network

- GA input data (accounts for all 3 platforms: mobile, tablet, desktop)
    - widgets represented as trees
        - GA uses tree operators
        - tree is generated from a set of bits and this set of bits is then available to GA for mutation, cross-over, etc.
        - leafs are large bit arrays (floats or integers?) => GA can use special operators
            - bit arrays from different leafs can mix with each other
            - e.g. http://www1.icsi.berkeley.edu/~storn/code.html
            - all widgets have a bounding box (equals to union of bbox of visual element and bbox of interaction element)
                - there are several additional non-widget bboxes (e.g. viewport, scroll_canvas, etc.)
        - overlapping widgets will have an x-y-sticky bit saying whether the widget shall stay where it is now even when moving in x or y directions (useful for toolbars, etc.)
        - cleaning/subtracting stage routines
            - some of these can be turned on/off by the GA itself
            - force keeping manually made changes (or at least the essence of them) to the design/widgets
                - most of the genomes will have it except for few to avoid local extremes
            - general constraints for UI as "cleaning rules"
                - e.g. totally avoid overlaps
                    - compaction for non-convex polygons; irregular shape packing; bitmap packing
                    - e.g. https://github.com/Jack000/SVGnest (it's good) or https://github.com/thierry7100/CutOptim (unsure how good it is, but it's ~8 years newer algorithm)
                - e.g. https://www.youtube.com/watch?time_continue=147&v=KJJlxdqg1Dc
                - e.g. https://darkpatternstipline.org/sightings
            - XPMA-tags based relationships between widgets
                - sets of widgets having the same property
                    - offset, height, width, color, transformation, rotation, scale, ...
                - sets of interleaving widgets
                - ...
    - data not to be evolved by GA bypass GA as independent values
        - physical dimensions range in meteres of the display width and height (mobile, tablet, desktop/beamer)
        - distance range in meters from which the result will be perceived

- fitness function is a neural network (NN)
    - https://pcc.cs.byu.edu/2017/10/02/practical-advice-for-building-deep-neural-networks/
    - TBCNN (tree-based convolutional neural network) for the tree structure
    - at the same time some ???-convolutional neural network to grasp all the single properties of a widget (color, offset, dimensions, ...)
        - do not try the following inputs (because the neural network will do it internally on its own)
            - any positional relationships between widgets like
                - euclidean distance between centroids
                - euclidean distance between approx. same-sized clusters of widgets (a cluster of smaller widgets versus cluster with one bigger widget)
            - "felt closeness between widgets" - imagine fuzzy clustering with criteria: color similarity, volume (width * height), narrowness-bulkiness scale, sparse-opaque scale, ...
    - output of the NN is without softmax (which is used for classification, but we need plain floats normalized to a predefined interval)
        - https://stackoverflow.com/questions/38319898/tensorflow-neural-net-with-continuous-floating-point-output

- for this to work we assume semi-interactive **UI designer tool**
    - with live animation of constantly growing & shrinking view of desktop, tablet, smartphone UIs
        - live means, that any manually made change to positional relationships will be immediately reflected
        - shall support scrolling (and remember the scrolling position)
    - this means all values changeable by this tool will have a flag designating whether the current value was set by hand or not
        - this flag will be obeyed by all GA stages

## 2D-visualisation (later 3D or more dimensions)

AI with a learning phase will be used (e.g. ML algorithm like SOMA).

**data set**

- a correct and working XPMA model (can be successfully executed - i.e. all data/mocups/skeletons are available)
    - requirement: the part of the model which is just for visual representation (e.g. button bitmaps/SVGs) has to be tagged accordingly
- sample of the visual representation
    - requirement: has to be first characterized properties (a human decision)
        - 3 animations (at least one of desktop, tablet, smartphone needs to be available otherwise the human decision makes no sense) of growing/shrinking UI
        - let people assess also purely generated designs in case there is a manually improved version which must then also get assessed by the same people (these "pairs" of designs will then be used specially by the GA - namely the originally generated design to train it and the manually improved version to provide error feedback for error backpropagation)
        - colors (independent from whether it's also done with geometrical objects or any other visual means) are (also) used to divide icons/widgets/tools to logical groups
        - subjective functional ("it does what it shall do" IMO) usability (best I know <-> nearly unusable)
        - subjective appearance (best I've ever seen <-> worst I've ever seen)
        - extent to which subjectively ergonomically "adjacent" inputs/outputs are also visually adjacent in the UI (it's not needed to uncover them or scroll or switch to a different tab or open a menu, etc.)
        - amount of nearly hidden (hardly visible/noticeable) or less conveniently reachable "widgets"
            - note hierarchy exists due to
                - tagging of tasks (this we know from XPMA)
                - collections (this we know from XPMA)
                - too few space on the canvas (this has to be completely introduced by the optimization algorithm)
        - extreme roundiness in the design (nothing is sharp) <-> no roundiness in the design (everything has sharp corners, there are no circles, etc.)
        - very modern design <-> rigid or old design
        - extremely pale design <-> extremely dark design
        - aerated design <-> very dense design
        - very colorful <-> strictly two colored
        - stimulative/energizing <-> calming
        - mutual alignment of items/widgets: not aligned at all (no item neither horizontally nor vertically aligned with any other item) <-> fully aligned (i.e. absolutely every single item fits full cells in an invisible coarse grained regular grid)
        - subjektivni mira designoveho grupovani (neplest se zanorovanim)
        - subjektivni mira zanorovani (neplest s grupovanim)
        - urci si pro Tebe subjektivne nejdulezitejsi prvky a ohodnot miru jejich dostupnosti
        - subjektivni mira celkove tezkopadnosti ovladani (vcetne logiky ovladani, neprijemnych prekvapeni a nachylnosti na chybne vstupy)
        - zastoupeni prosteho, malo stylovaneho textu na ukor vhodnejsi reprezentace (napr. obrazkove, piktogramove, ikonove, 3D, interaktivni, animovane, ...)
        - fits Microsoft design (Windows 10 or newer): not at all <-> completely like Microsoft products
        - fits Apple design (macOS, iOS, ...): not at all <-> completely like Apple products
        - fits Google design (Android): not at all <-> completely like Google products
        - somehow weird <-> actually not weird
        - extremely minimalistic (can't be more) <-> totally antiminimalistic
        - platforms (desktop, tablet, smartphone) absolutely inconsistent (look, behavior) <-> platforms fully consistent
        - fitting notions of previous steps where appropriate (e.g. I've touch-selected a picture from a list and now the picture is at the top of my screen and new content fills the rest 80% of the screen) <-> inappropriate or missing notion of previous steps
        - no unproductive activity (mouse movement, clicks to open hierarchies, clicks/movements to open tabs/etc., ) needed <-> everything I do mostly consists of unproductive activity
        - subjectively "fluid" pleasant experience <-> subjectively distractful & stressful experience
        - conventional <-> highly unconventional (e.g. artistic)
        - feels very modal (can't see/use many things right now without interaction) <-> totally non-modal (can see/use all things right now without interaction)
        - "background data structure" is immediately visible/clear after one user step (e.g. one mouse click) /e.g. dashboard/ <-> it is invisible (no dashboards; showing only the smallest possible record from the DB score very low)
        - FIXME some of these
            - Clean/simple – modern, minimalist
            - Classy – luxurious, erudite, classic
            - Friendly – casual, informal
            - Quirky – design-forward, creative
            - Techie – futuristic, geeky
    - the algorithm will take all the requirements into account (e.g. as weights - see ML boosting like XGBoost - it's just 2 SLOC in Python)
    - because we'll have missing data, we should use https://github.com/ufoym/imbalanced-dataset-sampler

Additional ideas on the **expected result of UI generation**

For each of the following properties (size, shape, ...) there will be a separate (deep) neural network.

The number of neurons in the output layer will be the same as in the input layer (hidden layers will be slightly bigger). The input layer will have for each "widget" type 10000 free slots. Any input will be first divided according to the "widget" types and then permuted so that all positions in a "widget" slot will get used equally. We assume we don't need to permute anything on the output as the neural network shall anyway produce plausible results.

Later in front of the customer we'll probably use transfer learning, which shall be fast enough for a near immediate UI generation - see e.g. https://popelka.ms.mff.cuni.cz/~hrach/smrst-2017/2017-12-02-hluboke-neuronove-site.mp4

- each XPM task must not necessarily correspond to "one viewport", but if the task is small, then there might be more tasks on one viewport, but visually separated from each other and all disabled until it's their turn in the process
- own/internal parameters of a "widget"
    - relative shape
    - relative volumetrical overlap (how much of the space it takes)
    - color (contrast has to be at least N)
    - special parameters of each "widget" (e.g. tabs on the top, tabs hidden under the 3-dot button menu, etc.)
    - animation (type, length, options...)
- relation to every single other object (a global canvas is also an object)
    - FIXME maybe use invariants in the following properties
    - tags in the XPMA model relating to visual representation (e.g. coupling)
    - relative size
    - size dynamics (fixed, linearly expanding/shrinking, non-linearly expanding/shrinking)
        - this is difficult to define for the UI specialist => skip any size dynamics completely and make everything implicitly linearly expanding/shrinking?
    - relative distances to significant points of other objects
    - relative volumetrical overlap (how much of the space it takes)
    - overlap precedence (something like z-index)
    - relative importance precedence ("what can be later down on the web page or what can be in a buried tab or in a popup window")
    - color (contrast has to be at least N)
    - relative amount of free space "around" (strong gaussian blur, then maybe thresholding, then maybe matching with the nearest simple geometrical object like a rectangle, then relative padding computation)
        - e.g. text will have a lot as most of the area is plain background
        - is this really needed as we have
    - good score with https://www.visualeyes.design/
- something which will ensure, that nothing will be too much hidden (1x1px on the screen is not nice)
    - remove/filter out most of those which include hidden features?

## Tests

- malo naucena sit
- prilis naucena sit (dava presny vysledek prakticky pro kazdy ucici sample, ale pro novy sample dela blbosti)
- mnozstvi neuronu v prostredni vrstve

## Training set

- https://www.wix.com/website/templates/html/all/19
- http://www.artisteer.com/?imsmp_templatesPage=3&p=website_templates&order=popular
- http://www.dotemplate.com/

## Target canvas types

                 | shorter observer distance | longer obs. dist.
-----------------+---------------------------+------------------
mobile           |           yes             |       no
tablet           |           yes             |       no
notebook &
desktop &
large projection |           yes             |       yes
