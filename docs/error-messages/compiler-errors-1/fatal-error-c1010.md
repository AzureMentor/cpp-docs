---
title: "Fatal Error C1010"
ms.date: "08/19/2019"
f1_keywords: ["C1010"]
helpviewer_keywords: ["C1010"]
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
---
# Fatal Error C1010

unexpected end of file while looking for precompiled header. Did you forget to add '#include name' to your source?

An include file specified with [/Yu](../../build/reference/yu-use-precompiled-header-file.md) is not listed in the source file.  This option is enabled by default in most Visual Studio C++ project types and *pch.h* (*stdafx.h* in Visual Studio 2017 and earlier) is the default include file specified by this option.

In the Visual Studio environment, use one of the following methods to resolve this error:

- If you do not use precompiled headers in your project, set the **Create/Use Precompiled Header** property of source files to **Not Using Precompiled Headers**. To set this compiler option, follow these steps:

   1. In the Solution Explorer pane of the project, right-click the project name, and then click **Properties**.

   1. In the left pane, click the **C/C++** folder.

   1. Click the **Precompiled Headers** node.

   1. In the right pane, click **Create/Use Precompiled Header**, and then click **Not Using Precompiled Headers**.

- Make sure you have not inadvertently deleted, renamed or removed header file (by default, stdafx.h) from the current project. This file also needs to be included before any other code in your source files using **#include "stdafx.h"**. (This header file is specified as **Create/Use PCH Through File** project property)