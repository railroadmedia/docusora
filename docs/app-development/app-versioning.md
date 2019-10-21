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

The concepts and incrementing rules are the same as android. The only differences are they are named differently and the build code uses the X.Y.Z format instead of just a single number. We should treat the build codes just like the single number on android and ignore the dot notation. For example version code 193 for android should be build code 0.1.93 for IOS. Version code 8377 would be 0.83.77 build code on IOS.

## Workflow

It's the responsibility of the developers and QA team to track which version codes align with what version names. For example 10 different builds with incrementing version codes may go through QA before we push a single new build with a new version name to users. The version name and version code should not be related in their numbering.

Here is an example of how version codes and version names will progress over time with a weekly release cycle:

Day 1 - we launch a new version to users:
- Version code: 26 (0.0.26 on IOS)
- Version name: 1.0.13

Day 2 - a new build is sent to QA with:
- Version code: 27 (0.0.27 on IOS)
- **Version name: 1.0.14**

Day 3 - a new build is sent to QA with:
- Version code: 28 (0.0.28 on IOS)
- Version name: 1.0.14

Day 4 - a new build is sent to QA with:
- Version code: 29 (0.0.29 on IOS)
- Version name: 1.0.14

Day 5 - a new build is sent to QA with:
- Version code: 30 (0.0.30 on IOS)
- Version name: 1.0.14

... can go on indefinitely.

Day 10 - previous build passes QA and is launched to users with versions set to:
- Version code: 36 (0.0.36 on IOS)
- Version name: 1.0.14

Day 11 - a new build is sent to QA with:
- Version code: 37 (0.0.37 on IOS)
- **Version name: 1.0.15**

Day 12 - a new build is sent to QA with:
- Version code: 38 (0.0.38 on IOS)
- Version name: 1.0.15

Day 13 - a new build is sent to QA with:
- Version code: 39 (0.0.39 on IOS)
- Version name: 1.0.15

... can go on indefinitely.
 
Day 100 - previous build passes QA and its a large project launch. It's launched to users with version set to:
- Version code: 126 (0.1.26 on IOS)
- Version name: 1.1.0

Day 101 - a new build is sent to QA with:
- Version code: 127 (0.1.27 on IOS)
- **Version name: 1.1.1**

Day 102 - a new build is sent to QA with:
- Version code: 128 (0.1.28 on IOS)
- Version name: 1.1.1

Day 103 - a new build is sent to QA with:
- Version code: 129 (0.1.29 on IOS)
- Version name: 1.1.1

etc...