name: Fractally Meeting Primitives  
version: 1  
description: JSON-formatted meeting format suggestion  
author(s): Douglas Butner (Telegram: godsolislove, [linktr.ee/iammonlove](https://linktr.ee/iammonlove))  


# Abstract

Meetings in Fractally currently provide no structure to the format of the meeting, and no mechanism to record important information about the meeting. Important information is that which may affect the decisions of a stakeholder in the future. This seed will address a solution that may be implemented, or referred to when developing the final solution. 

# Detailed Explanation

## Meeting Primitive 
- Json structure that contains all the important information about a meeting including attendees, their votes, funds allocations, and record of work that was contributed. 
- A system in place to challenge others who claim work or an association that isn't valid. This system is outside of scope of this document.

## Justification of Importance 

**Attendees** - A record of attendees can be used to incentivize attendance outside of the internal mechanisms, including tracking attendance for additional rewards if a member shows up to a threshold number of meetings in a row. 

**Votes** - Tracking votes allows for a measure of collusion that can be applied algorithmically. Conversely, it can show loyalty to a particular person, or type of work (builders value code more, investors value viral content, etc)

**Work Contributed** - A short description of the work (1-2 sentences) allows members to decide whether or not a user has already been compensated for given work. It also allows a member who did the work to prepare in-meeting or before a list of what work they did this week. With a graphic display on gofractally, voting members have a quick reference so they remember what everyone did and their names without asking.


# Data structure 

This data structure holds an [associative] object containing 2 objects, attendees and meeting. It may be better to expand this to have one

Attendees object can be made with or without a human primitive. We will use a sample of a human primitive object because no other form has been proposed. 
 
 This data is for each round of the meeting, not a whole days worth. 
 
 ```
// --- Meeting Primative JSON --- \\

// Please send a pull request to improve this structure

{
meeting: {
  start: 71237498709425, // Timestamp of scheduled start time
  consensus: 1 // Bool set to if consensus was reached in the group. 
}
attendees: {
  [
    human: { // This is an example "Human primitive"
      name: "Legal Name F+L",
      organizations: "Associated Organizations", // Should eventually be improved
      contributions: "This is a 256/512 char summary of the work done that each person can submit ahead of time on gofractally.",
      updated: 124387123 // Timestamp of last update to be sure user's contributions are this week
    }, 
    voted : [ // This can be an ordered array, associative array (JS) or object
      "mypickrank1",
      "mypickrank2",
      "mypickrank3",
      "mypickrank4",
      "mypickrank5",
      "mypickrank6"
    ]
  ]

}
} //END 
```

## Extending this structure

This structure could be extended to add things like the user's last week rank, but that information can be extrapolated from older information, and only information that relies on new information about the current meeting itself should be added.

# Actionable Steps

Use this data structure either directly, or as a guide to build a table on EOSIO / HIVE, or both.

Route 1 (Quick, efficient, centralized)
- Incorporate a UI that allows members to fill out a form with their votes, and an array of short text describing their contributions
- Once in a group (may require groups based on on-chain RNG) the gofractally UI shows a vertical list of draggable UI elements that then can populate a transaction's data object for the user's rankings. 


# Timeline

- Q1 2021 - Initial Discussion in community meetings
- Q2 2021 - First implementation 
- Q3 2022 - Improvements +tweaks

# Success Metrics

- Shortening time to reach consensus (Objective)
- More meeting information recorded + accessible (Objective)
- Easier acces of data by developers (Objective + Subjective)
- Better self-evaluation of informedness before meetings (Subjective)


# Mini changelog

## Version 1 - 2022-03-13
### Added 
Initial Commit
### Removed 
### Changed
### Fixed
