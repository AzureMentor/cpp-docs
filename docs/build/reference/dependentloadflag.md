---
title: "/DEPENDENTLOADFLAG (Set default dependent load flags)"
description: "The /DEPENDENTLOADFLAG option sets default flags for DLLs loaded using LoadLibrary"
ms.date: "05/18/2018"
f1_keywords: ["dependentloadflag"]
helpviewer_keywords: ["LINK tool [C++], dependent load flags", "-DEPENDENTLOADFLAG linker option", "linker [C++], DEPENDENTLOADFLAG", "DEPENDENTLOADFLAG linker option", "/DEPENDENTLOADFLAG linker option"]
---
# /DEPENDENTLOADFLAG (Set default dependent load flags)

Sets the default load flags used when `LoadLibrary` is used to load DLLs.

## Syntax

> **/DEPENDENTLOADFLAG**[**:**_loadflags_]

### Arguments

*loadflags*<br/>
An optional "C"-style 16-bit integer value in decimal, octal with a leading zero, or hexadecimal with a leading `0x`, that specifies the dependent load flags to apply to all [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) calls. The default value is 0.

## Remarks

This option is new in Visual Studio 2017, and applies only to apps running on Windows 10 RS1 and later versions. This option is ignored by other operating systems that run the app.

On supported operating systems, this option has the effect of changing calls to `LoadLibrary("dependent.dll")` to the equivalent of `LoadLibraryEx("dependent.dll", 0, loadflags)`. Calls to [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) are unaffected. This option does not apply recursively to DLLs loaded by your app.

This flag can be used to prevent DLL planting attacks. For example, if an app uses `LoadLibrary` to load a dependent DLL, an attacker could plant a DLL with the same name in the search path used by `LoadLibrary`, such as the current directory, which may be checked before system directories if safe DLL search mode is disabled. Safe DLL search mode places the user's current directory later in the search order, and is enabled by default on Windows XP SP2 and later versions. For more information, see [Dynamic-Link Library Search Order](/windows/win32/Dlls/dynamic-link-library-search-order).

If you specify the link option `/DEPENDENTLOADFLAG:0xA00` (the value of the combined flags `LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`), then even if safe DLL search mode is disabled on the user's computer, the DLL search path is limited to protected directories that are more difficult for an attacker to change. For information on the flags available, and their symbolic and numeric values, see the *dwFlags* parameter description in [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw).

### To set the DEPENDENTLOADFLAG linker option in the Visual Studio development environment

1. Open the project's **Property Pages** dialog box. For details, see [Set C++ compiler and build properties in Visual Studio](../working-with-project-properties.md).

1. Select the **Configuration Properties** > **Linker** > **Command Line** property page.

1. Enter the option in **Additional Options**.

### To set this linker option programmatically

- See <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## See also

- [MSVC linker reference](linking.md)
- [MSVC Linker Options](linker-options.md)
- [Link an executable to a DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [Link an executable to a DLL](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)
- [Dynamic-Link Library Search Order](/windows/win32/Dlls/dynamic-link-library-search-order)
