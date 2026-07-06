---
title: 'A Digital Microscopy Counter: Keyboard-Driven Web Application for Rapid Counting and Data Integrity Stewardship'
tags:
  - arbuscular mycorrhizal fungi
  - root colonization
  - web application
  - microscopy
  - soil ecology
authors:
  - name: Sedona Marie Spann
    orcid: 0009-0006-9844-1235
    affiliation: "1"
affiliations:
 - name: School of Earth and Sustainability, Northern Arizona University, Flagstaff, Arizona, United States
   index: 1
date: 25 June 2026
bibliography: paper.bib
---

# Summary

Quantifying fungal root colonization is a foundational task in plant-soil ecology. 
Current methods commonly rely on physical hand counters necessitating post hoc manual data transcription, 
which is inherently inefficient and introduces potential error. 

The *Radical Root Colonization Counter*, a lightweight web application, was designed 
to streamline grid intersect root scoring. This tool enables rapid counting 
using personalized keyboard key combinations, audio feedback for quality control, 
customizable counter categories, and automated session data recording. 
Each sample count is stored locally and can append, or be exported as, a csv file 
ready for statistical analyses. 

By removing manual transcription, adding immediate audio confirmation of structures recorded, 
and streamlining data input as well as output, this application improves the efficiency 
and data integrity of human-counted root colonization workflows.
The design process of this tool also demonstrates the utility of iterative, user-driven development 
supported by AI-assisted prototyping in the creation of specialized tools used for improving research methods.

# Statement of Need

Quantification of root colonization is an informative and often cost effective metric
 in studies of plant-microbe interactions and soil ecosystem function [@Brundrett:2009]. 
 ‘Grid intersect scoring methods’ such as [@Trouvelot:1986] and [@McGonigle:1990] methods 
 are based on visual assessment of a representative subsample of root segments under compound microscope. 
 Observed fungal root-colonizers vary by experiment but are broadly classified by Arbuscular Mycorrhizal Fungal (AMF) 
 Structures, dark septate endophytes (DSE), non-am hyphae, plasmodiophorids, and olpidium structures. 
 Counting is often done on hand counters followed by transcription of those counts onto a paper worksheet 
 or directly into a digital spreadsheet.

Grid intersect methods have several limitations. First, each button on a hand counter corresponds to a structure, counter buttons are often being relabeled in a shared lab based on personal preference and an experiment's ‘structures-present’ specificity. This can add time to set up when button locations must be relabeled between scoring sessions. Second, transcription of counts from paper into digital datasets is time-consuming and introduces opportunities for scribal error. Third, all buttons produce the same “click” sound, which can increase error at speed because the sound confirms a button press, but not necessarily the correct button. Furthermore, both new and old hand counters are known to erroneously ‘click’ yet not add to a count, therefore best practice necessitates looking up from a slide to make sure the counter has counted, adding unnecessary mental load and seconds to every intersection (a single root count). Seconds become minutes when the user has 100 - 200 root intersections to count for a single sample.

To address these shortcomings, the *Radical Root Colonization Counter* was developed, a browser-based web application designed to facilitate rapid and specialized scoring techniques enabling the generation of data ready for statistical analyses without transcription. This tool places an emphasis on minimal technical interaction, real-time audio and visual feedback, and instant generation of structured datasets.

# State of the Field

Innovative tools, such as AMFinder [@Evangelisti:2021], can digitally "score" root images by quantifying all fungal structures within an entire sample or slide, often with greater accuracy than traditional grid-intersect methods. However, this approach requires users to scan or photograph each slide and have the technical proficiency to operate the software. Therefore the decision is often made to use the common, human-scored, grid intersect methods. There is an inspiring abundance of research into the computational automation of human-scoring, yet an absence of simple, customizable digital tools tailored to the widely used human-scoring workflow.

# Software Design

The primary design goals were to facilitate highly specialized scoring needs with customizable button options, maintain visual focus on the microscope slide by minimizing user interaction during scoring, create audible confirmation of specific button presses, and provide structured data output. Many of these features were borne of invaluable input and suggestions from lab mates testing and retesting software prototypes.

The Counter is implemented as a single web page. It runs entirely within a web browser and all data is stored locally avoiding installations, server infrastructures, or internet connectivity. Additionally, all components are platform-native browser APIs making this a zero-dependency web tool.

Each counter is mapped to fixed keyboard keys of the user’s choosing, with some presets (eg., Q-M, F1-3), enabling rapid input without mouse interaction. This allows users to memorize personally optimal key locations to maintain continuous visual focus on the roots while scoring.

Each ‘count’ triggers the spoken numeric value that the category has reached followed by the name of the category. This provides immediate confirmation of input without requiring visual verification. Root colonization in the NAU Soil Ecology Lab is complete after 100 or 150 ‘intersections’ therefore a song is played when the user reaches these totals.

The application appears in two interface modes housed in the ‘Looks & Sounds’ menu. Users can edit counter names colors and order to match specific scoring schema when toggled out of "Minimal Mode" (reffered to as "Full Mode" in the source code). Toggle to "Minimal Mode" and the app presents large, simplified counters optimal for rapid scoring \autoref{fig:1}.

![A simple McGonigle method counter template would include these categories, shown here in ‘minimal mode’ and ‘light mode’.\label{fig:1}]
(H:/AMF-Colonization-Counter/figure1.png)

If the user would like to score using the more accurate yet often more time consuming Trouvelot method wherein colonization intensity is captured using a ranking system of 1-5 for specified fungal structures [@Kokkoris:2019]; the categories could be as follows in \autoref{fig:2}.

![A Trouvelout method counter template would include these categories, shown here in ‘full  mode’ and ‘dark mode’.\label{fig:2}]
(H:/AMF-Colonization-Counter/figure2.png)

Each slide is treated as a discrete score. The application automatically records the date and the duration of the score from the first counter press up to when saved. This enables time tracking for each score to help the user control time spent on each slide.

"Counter Configurations" and score histories are stored locally in the browser so an exporting function was integrated and is housed in the "Tools" menu. Scores can be exported as a pivoted CSV file and Counter Configurations can be saved as json files making them portable and shareable across systems via simple file transfers. Scores can also be appended to a chosen dataset, minimizing the risk of accidental overwriting. Moreover, Historical scores retain their original counter names, even if counter configurations are later modified. A sample is only named after scoring, this encourages ‘blind scoring’ to prevent unconscious confirmation bias [@Kardish:2015]. ‘Blind scoring’ is accomplished by preventing the microscopist from seeing a sample’s treatment labels until after scoring is complete, only then is the sample name revealed and recorded. When ‘save score’ is pressed two pop-up’s ask in succession what to name a sample and if there are notes for the sample, encouraging the user to record anything novel for each sample.

# Research Impact Statement

The *Radical Root Colonization Counter* was developed as a tool to assist in the colonization quantification of one project but has grown to be tested and used and by many others in the soil lab. It provides a simple, accessible solution for rapid and standardized root colonization scoring. By integrating keyboard-based input, real-time feedback, and structured data export, the counter reduces cognitive load, minimizes error, and improves efficiency. The keyboard-driven interface reduces hand movement and minimizes interaction. Audio feedback further reduces the need for visual confirmation, supporting efficient scoring. By eliminating manual transcription and enabling real-time data capture, the application reduces total processing time from observation to analysis-ready dataset. Direct digital recording of counts reduces transcription errors and standardizes data structure across scores. This application demonstrates the potential of developing lightweight digital tools to enhance data collection in ecological research.

# AI Usage Disclosure

LLM-assisted code generation with Claude, ChatGPT and Gemini was used to accelerate implementation, without requiring formal HTML software training. However, domain expertise was essential for defining requirements, validating functionality, and ensuring feature relevance for practical scoring [@Peng:2023]. The application was developed using an iterative, user-driven design process focused on usability during microscopy. Development proceeded through prototyping cycles, with features added and refined based on human testing of the tool while scoring.

# Availability and Usage

The *Radical Root Colonization Counter* is freely available as a browser-based web application: 
[Radical Root Colonization Counter](sedonams.github.io/AMF-Colonization-Counter).
The software can also be downloaded and distributed as a standalone HTML file: 
[Radical Root Colonization Counter Source Code](github.com/Sedonams/AMF-Colonization-Counter).

# Acknowledgements

Financial support was provided by the US Department of Energy program in Systems Biology Research to Advance Sustainable Bioenergy Crop Development grant DE-SC0021386 (DE-FOA-0002214). Thanks to Dr. Beatice Bock for literary encouragement, Callum Rohrer for constructive feedback during beta testing, Dr. Nancy Collins Johnson for advising, and all the NAU Soil Ecology Lab technicians who continue to provide refinement suggestions.

# References