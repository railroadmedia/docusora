# App Versioning Guide

## Android

*Reference: [https://developer.android.com/studio/publish/versioning](https://developer.android.com/studio/publish/versioning)*

There are 2 types of versions for an android mobile app:

- **Version Code**
- **Version Name**

**Version code** is an internal version number which is only used to track if one build is versioned higher than another. It's a single integer number. This number should be incremented by 1 with any new build that is sent to QA. This number is not relevant to the user and should not be displayed to the user in the app or in the app store. 

**Version name** is a standard X.Y.Z version number which is displayed in the app store and to users. Anytime a build is sent to users the version name should change (be incremented). 

X: will be incremented with large overhauls or project launches. The project manager will decide when this number should be incremented and will inform the developers.

Y: will be incremented with small project launches and feature updates. The project manager will decide when this number should be incremented will inform the developers.

Z: will be incremented for each new patch of bug fix build that is sent to users through the app store. For example, if we push a new build to users once a week this number should increment by 1 every week.

## IOS

*Reference: [https://developer.android.com/studio/publish/versioning](https://developer.android.com/studio/publish/versioning)*

There are 2 types of versions for an IOS mobile app:

- **Build Code** == (Version Code)
- **Version Number** == (Version Name)

The concepts and incrementing rules are the same as android. The only difference is they are named differently.

## Workflow

It's the responsibility of the developers and QA team to track which version codes align with what version names. For example 10 different builds with incrementing version codes may go through QA before we push a single new build with a new version name to users. The version name and version code should not be related in their numbering.

Here is an example of how version codes and version names will progress over time with a weekly release cycle:

Day 1 - we launch a new version to users:
- Version code: 26
- Version name: 1.0.13

Day 2 - a new build is sent to QA with:
- Version code: 27
- Version name: 1.0.14

Day 3 - a new build is sent to QA with:
- Version code: 28
- Version name: 1.0.14

Day 4 - a new build is sent to QA with:
- Version code: 29
- Version name: 1.0.14

Day 5 - a new build is sent to QA with:
- Version code: 30
- Version name: 1.0.14

... can go on indefinitely.

Day 10 - previous build passes QA and is launched to users with versions set to:
- Version code: 36
- Version name: 1.0.14

Day 11 - a new build is sent to QA with:
- Version code: 37
- Version name: 1.0.15

Day 12 - a new build is sent to QA with:
- Version code: 38
- Version name: 1.0.15

Day 13 - a new build is sent to QA with:
- Version code: 39
- Version name: 1.0.15

... can go on indefinitely.
 
Day 100 - previous build passes QA and its a large project launch. It's launched to users with version set to:
- Version code: 126
- Version name: 1.1.0

Day 101 - a new build is sent to QA with:
- Version code: 127
- Version name: 1.1.1

Day 102 - a new build is sent to QA with:
- Version code: 128
- Version name: 1.1.1

Day 103 - a new build is sent to QA with:
- Version code: 129
- Version name: 1.1.1

etc...