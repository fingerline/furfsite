# Furfsite

This document will serve as the basis for development on the website for the Furred Fleet static on FFXIV, as well as the accompanying (as of yet unnamed) Discord bot. It will account for general plans for features, candidates and requirements for frontend design, and plans for the architecture of the project as a whole.

Please note that the word "static" will be used throughout this document. This is as in "unmoving, unchanging" broadly, rather than to specifically refer to the FURF static raiding group. From this point forward, if the text must refer to the FURF static raiding group, it will refer to it as "FURF" or the entire phrase rather than any use of the word "static".

- [Furfsite](#furfsite)
  - [General Overview](#general-overview)
    - [Design Goals](#design-goals)
    - [End-of-Development Plans](#end-of-development-plans)
  - [Features in Detail](#features-in-detail)
    - [Static Features](#static-features)
      - [Mechanic Details](#mechanic-details)
      - [Fight Footage Archive](#fight-footage-archive)
      - [FFLogs Archive](#fflogs-archive)
    - [Dynamic Features](#dynamic-features)
      - [Loot Tracker](#loot-tracker)
      - [Progress Tracker](#progress-tracker)
      - [Make a Group](#make-a-group)
      - [Calendar and Raid Night Signups](#calendar-and-raid-night-signups)
      - [Fight Planning Tools](#fight-planning-tools)
  - [Architecture](#architecture)
  - [Plans for Development](#plans-for-development)
  - [Recap](#recap)

## General Overview

The site will be a resource to compile useful information for FURF in lieu of using a series of occasionally-updated discord pins across a variety of channels. These static resources include, but are not limited to:

- Strategy diagrams and descriptions per mechanic
- Uploaded fight footage
- Archive of FFLogs uploads with at-a-glance details

Beyond relatively static resources, the site wil provide more dynamically generated or programmatic tools in order to better facilitate raid nights and the planning thereof.

- Calendar and signup functionality for raid nights
- Fight planning tools
- Loot tracking functionality for quick loot distribution
- Progress tracking
- "Make a group" tool for nonstandard group compositions

These lists are not necessarily comprehensive. It is worth noting that the dynamic tools will take longer to develop than the static archival functions. The site will be evolving significantly over time in both form and function as development and feedback take place.

As an addition to the main site, there are currently plans to develop a small discord bot to make some of this information more easily available to members who do not wish to access the site independently, and to facilitate in-raid use without having to open up any other programs.

### Design Goals

The construction of every portion of this project should aim to adhere to some simple design philosophy goals.

1. Avoid redoing others' work.
  
    There's a lot of work out there done for web technologies related to FFXIV by people with a ton of experience, as well as plenty of resources for both gameplay and analysis. It would be a disservice to the users of this project to opt to withhold good resources that already exist in favor of doing it ourselves.

    This should not be at the expense of the gameplay, however. A big part of what FURF does relies on blind progression and improving independently. If the site were to rely on incorporating external resources on gameplay too heavily, the entire project would become redundant-- after all, very popular sites already exist to compile resources from content creators for these fights.

2. Focus on readability and ease of use.

    The biggest barrier to adoption for something like this is getting people to learn the tools it provides. As it stands, most of the core functionality of this project already exists in the form of Discord pinned messages. This project's offer to the user is to make that information easier and faster to find, use, and display. Every design decision should be made with this in mind.

    Likewise, speed of use for an inexperienced user should be prioritized. After all, spending a bunch of time inputting extremely specific values into a form is a hard sell if the reward is saving a few seconds of fumbling around after a pull. By the nature of this project's subject, there will need to be some manual user interaction to get the system the data it needs; making that process as fast and accessible as possible is extremely important to make sure everyone takes part, and as a result, benefits.

3. Balance complexity across similarly important features.

    Avoid getting trapped in overengineering a feature when there's more work to be done. Not only does balancing the level of complexity of each component of a project make the project feel less lopsided, but it also helps to make sure the project is eventually completed at all.

    There is one portion of the site that has the potential to have an overly-long development process, that being the "Fight Planning Tools". This component could very well be a small project on its own, but it's a tool that very clearly has a need in FURF.

### End-of-Development Plans

While this project is certain to be deeply entwined with the individual needs of FURF, there is an eventual possibility that the software this site is built from could eventually be repurposed for general use for other raiding groups, should they wish to have a similar tool. This is not anticipated to get much traction in the wider FFXIV community, if any at all. This goal is simply to further the author's pursuit of deepening their understanding of software development, and making software for general, public use.

## Features in Detail

### Static Features

#### Mechanic Details

The foremost desirable feature for archival will be the ability to organize and make available detailed explanations and diagrams for mechanics in certain raiding scenarios.

This feature will:

- Provide members with a complete archive of uploaded mechanic explantions and diagrams/image resources for mechanics in the fight
- Allow easy access to exploration and viewing of specific mechanics, avoiding cluttering or confusion at all costs
- Provide an individual view for each archived mechanic to allow for reference
- Allow easy upload, editing, and deletion of fight mechanics
- Provide a mechanical overview "Quick Reference" page for each fight.

This feature will not:

- Automatically document fights.
- Allow community submissions to be pushed directly to the overview.
  
  This is to avoid making appropriate resources difficult to find. The only resource a user should be able to find without specifically looking for it (if at all) is the accepted "master" copy of the resource. This will require some sort of approval/integration system.

- Person-or-user tailoring for content.
  
  This will make it more difficult for the resource to be used by someone just coming into the fight, such as a sub or for a reclear with a nonstandard group composition.

#### Fight Footage Archive

This feature will possibly be related to the Mechanic Details feature, but deserves its own discussion because of its major utility outside of the context of learning a fight. This is not necessarily something that needs to be enforced for every pull, or even every raid night. This content will be added to the site at the rate at which it is captured and submitted for upload.

This feature will:

- Provide an easily searchable record of past recorded kills. Videos should be tagged and sorted by their PoV, fight, and progression/reclear status.
- Allow uploaders to provide a description independent of the description on YouTube.

There are no plans for this feature to do anything other than provide a central location to browse and archive links to submitted raid captures. There is no hosting happening here, no comment features, nothing. This resource is primarily available as independent reference material for individuals wishing to see a fight in action. Videos included in this archive may be inserted into the Mechanic Details feature, but there are no plans to automate this process nor enforce it.

#### FFLogs Archive

This feature will provide users with the ability to explore past FFLogs uploads for FURF. These uploads will not be submitted manually-- rather, they will be automatically collected when they are uploaded by members of the group. The automatic nature of this feature will likely be handled by a seperate functionality to the site itself, most likely being conjoined with the bot that mentioned previously as a portion of the project. This feature will:

- Automatically archive all FFlogs postings from designated members of the group related to the FURF raiding group.

  The method by which this will be achieved is still under consideration. It should be noted that whatever the solution should be, it should fulfill the criteria of not needing the uploader to upload the ACT log more than once (whether that be through the FFLogs uploader or indirectly), and not automatically uploading logs that are unrelated to the FURF raiding group.

- Provide "at-a-glance" details for a given log.

  This may entail a "thumbnail" for each log to show simplified performance details for each member before delving into general log details.

This feature will not:

- Analyze logs automatically or offer indirect analysis tools on its own.

  While the details within an FFLogs posting are important and of interest to FURF members, this program dods not aim to replace FFLogs functionality in any way other than providing brief overviews without needing to go to the site itself. This extends to other existing tools that rely on FFLogs such as XIVAnalysis, though it is possible that a link to the XIVAnalysis URL for a clear will be provided.

- Give detailed information regarding the contents of the log.
  
  As stated previously, this project will be avoiding entirely replacing FFLogs functionality. This will be expressed by there not being a "details" page associated with any given log, instead, the "at-a-glance" information will likely provide a drop-down of some key performance points for the members in the raid as well as general fight information. Every other detailed piece of information is much more suited to being read on the already-incredible FFLogs site.

### Dynamic Features

#### Loot Tracker

This feature will allow the raid to quickly determine the candidates for armor and loot drops. This will entail keeping track of what each person in the raid is actually wearing for their main class, as well as any subclasses that are registered within the system.

Completing this goal will additionally require information on BiS loadouts for each individual in the raiding group. This information will be submitted manually by group members.

This feature will:

- Provide a quick and readable output for who should be contending for loot for a given fight.
  
  This will require knowledge of the drop table for a fight before the fight, as well as the actual drops after the fight is clear. Luckily, this information is extremely easy to input when a fight is cleared through a clickable GUI.

- Allow external overview of a given character's loadout for a class, and provide insights into content needed to progress to BiS.

  The Lodestone site is frustratingly unable to provide users access to other's gear profiles beyond the gear that was equipped by the time the poll was completed. To combat this, users must manually input some of this information. This should not be labor intensive on the user's side or require any sort of technical know-how in order to increase accessibility. Much of this will be automated as loot is distributed using the feature.

  Users' path to BiS should be available through their profile through comparison of their gear and the BiS set in the system for their class.

- Allow users to update their own gearsets easily and without technical know-how.

This feature will not:

- Automatically collect gear information for users.
  
  This is unfortunately impossible as there is no official FFXIV API, and the Lodestone updates too slowly and with too little information to be helpful for this purpose. Likewise, there will be no Balance scraping. The site is still under construction and is largely incomplete and out of date.

- Provide incremental analysis for gearsets and lootdrops.

  While manually inputting BiS information once a tier is entirely reasonable, incremental analysis of the benefit of given gear pieces would require a massive amount of external information that would require user input beyond what is reasonable to expect from the target audience, who is not expected to spend more than five minutes interfacing with the site at a time.

#### Progress Tracker

This will be a small, primarily manual function of the site. This feature is intended to provide visualization of progress through given sets of raid progress, possibly on a user-to-user basis. Tracked progress will be things like completion of Extremes and Raid Tiers, both current and past.

This feature will:

- Provide FURF-wide raid progression tracking as an expression of achievement.

  This will likely be a component of the home page.

- Provide character-by-character progression tracking as an expression of achievement, as well as a planning tool.

  This will likely be a component of the individual character profile portion of the project.

This feature will not:

- Automatically update progress based on achievements.
  
  This may turn into a feature in the future. As it stands, it seems difficult to get information regarding achievments from the Lodestone for characters.

#### Make a Group

The "Make a Group" tool will serve two purposes: to facilitate substitution selection, and to provide alternative raid formations based on the list of desired roles users provide the system.

This feature will:

- Produce a set of possible arrangements for the group based on user parameters.
  
  Layouts should be ordered by "suitability" and produced based on the priority list of roles supplied to the group.

- Optimize group composition for group layouts that require a substitution.

  Layouts in this mode should be made to try and maintain the highest level possible of "suitability" while prioritizing lower-impact roles for an open space to bring in a substitute. Standin members should also be able to be inserted into the tool to specify if an available sub only plays a higher-impact role.

#### Calendar and Raid Night Signups

This tool will replace the current system by which FURF polls the raiders for their availability for a given raid night. This will be integrated with the Discord bot to enable users to give indication of their availability for a night through Discord, rather than needing to rely on users navigating to the site.

This feature will:

- Poll users for their availability during a given raid night.
- Give advanced warning to the group if there is a missing member.

  This advanced warning will provide a possible sample composition from the Make a Group function.

- Automatically remind users of upcoming raid nights.
- Allow users to create side events that do not take place during established raid times, as well as automatically recur raid nights.
- Allow all scheduling actions to take place using the provided Discord bot without needing to access the site.
- Allow users to opt-out of previously opted-in events.

- Provide a simple calendar of upcoming events for the home page.

#### Fight Planning Tools

This tool will allow easy access to planning out simple aspects of fights between raids. This tool is primarily intended to determine a schedule for damage mitigation, however, it should be able to be used for other scheduled aspects of play like healing or other  mechanical balancing acts.

This feature will:

- Allow a user to create a timeline of a fight and create an action timeline for an aspect of the fight.

- Visualize windows affected by actions taken during the fight to better allow for planning.

  This will show the length of time an action taken by the group will affect the fight. This is helpful for things like nonstandard mitigations that could possibly cover multiple mechanics, as well as give an indication of when certain delayed effects will come into play for spells such as Earthly Star and Microcosmos.

- Save schedules for fights, and allow them to be edited.

This feature in particular is very expandable and will require a large amount of development time as it is particularly unlike any other portion of the project.

## Architecture

At the time of thie document's initial writing, the site itself is planned to be hosted on Heroku's Free Tier as a Django project using a postgreSQL database. This is likely to change over the course of the project as the requirements and desired functionality change to outgrow the limitations provided by the use of Heroku.

Heroku sets several limitations on a Free Tier user's capabilities. The most pressing are the limits on waking time and storage. Storage is unlikely to be a problem for a while, as there are not functionalities that require an excessive amount of storage space at present, either in the form of physical size or database rows. There are limitations on process types as well, though these limitations will only come about if the Discord bot will require unanticipated processes. In the case that this does occur, the Discord bot can be hosted in another location.

The method by which the frontend will be constructed is still under consideration. React.js is the primary consideration.

## Plans for Development

Most systems involved in this site requre little interoperability, so development does not need to take place in any particular order (for the most part). That being said, there are certain higher or lower priority features of the site that will influence the order of development.

High priority tasks will be constructing the database and behavior for the endpoints for core features. The priority of features from high to low, are as follows:

1. Loot Tracker
2. Mechanic Details
3. Calendar and Raid Night Signups
4. FFLogs Archive
5. Fight Footage Archive
6. Make a Group
7. Progress Tracker
8. Fight Planning Tools

Again, this is not necessarily the order these features will be developed or completed in.

There is also the matter of the Discord bot, which is integral to the accessibility of this site's feature set. Initial setup of the Discord bot should be established early, as many of the features anticipate access through the Discord bot.

This bot will be highly customized for the FURF server. Many of its planned functionalities are not essential for the operation of the site. For this reason, complex necessary behavior will be developed alongside the respective feature, and all other functionality will be included as time allows, in no particular order.

## Recap

The site will serve as a resource collection hub for the FURF static raiding group, and will provide several tools to make preparing for raid, loot management, scheduling, and fight planning easier. The site will aim to be as accessible and fast to use as it possibly can, and will incorporate a Discord bot to aid in that endeavor.
