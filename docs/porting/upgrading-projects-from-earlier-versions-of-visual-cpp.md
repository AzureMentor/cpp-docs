---
title: "Upgrading Projects from Earlier Versions of Visual C++"
description: "How to upgrade Microsoft C++ projects from older versions of Visual Studio."
ms.date: "05/03/2019"
helpviewer_keywords: ["32-bit code porting", "upgrading Visual C++ applications, 32-bit code"]
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
---
# Upgrading Projects from Earlier Versions of Visual C++

In most cases, you can open a project that was created in an earlier version of Visual Studio. However, to accomplish this, Visual Studio upgrades the project. If you save this upgraded project, it cannot be opened in the earlier version.

> [!IMPORTANT]
> If you try to convert a project that was already converted, Visual Studio asks for confirmation because reconversion deletes existing files.

Many upgraded projects and solutions can be built successfully without modification. However, some projects might require changes to settings, source code, or both. We recommend that you use the following guidelines to address the settings issues first, and then if the project still doesn't build, you can address the code issues. For more information, see [Overview of potential upgrade issues](../porting/overview-of-potential-upgrade-issues-visual-cpp.md).

1. Make a copy of the existing project and solution files. Install the current version of Visual Studio and the earlier version side by side so that you can compare versions of the files if you want to.

2. In the current version of Visual Studio, open—and thereby upgrade—the copy of the project or solution and save it.

3. For each converted project, open the shortcut menu and choose **Properties**. Under **Configuration Properties**, select **General** and then for **Platform Toolset**, select the current version. (For example, for Visual Studio 2017, select **v141**.)

4. Build the solution. If the build fails, modify the settings and rebuild.

Data sources are contained in a separate database project so that you can more easily modify and debug the stored procedures in those sources. If you upgrade a C++ project that contains data sources, a separate database project is automatically created.

For information about how to update the targeted Windows versions, see [Modifying WINVER and _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md).

## In this section

[Upgrade your code to the Universal CRT](upgrade-your-code-to-the-universal-crt.md)<br/>
[Modifying WINVER and _WIN32_WINNT](modifying-winver-and-win32-winnt.md)<br/>
[Fix your dependencies on library internals](fix-your-dependencies-on-library-internals.md)<br/>
[Floating-point migration issues](floating-point-migration-issues.md)<br/>
[Use native multi-targeting in Visual Studio to build old projects](use-native-multi-targeting.md)<br/>
[Visual C++ features deprecated in Visual Studio 2019 preview](features-deprecated-in-visual-studio.md)<br/>
[Build System Changes](build-system-changes.md)

## See also

[What's New for Visual C++ in Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Visual C++ change history 2003 - 2015](../porting/visual-cpp-change-history-2003-2015.md)<br/>
[Nonstandard Behavior](../cpp/nonstandard-behavior.md)
