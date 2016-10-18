---
title: "How to: Convert an Existing MFC Ribbon to a Ribbon Resource"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ribbon resource, converting from an MFC ribbon"
  - "MFC ribbon, converting to a ribbon resource"
ms.assetid: 324b7ff6-58f9-4691-96a9-9836a79d0fb6
caps.latest.revision: 6
ms.author: "mblome"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# How to: Convert an Existing MFC Ribbon to a Ribbon Resource
Ribbon resources are easier to visualize, modify, and maintain than manually coded ribbons. This topic describes how to convert a manually coded ribbon in an MFC Project into a ribbon resource.  
  
 You must have an existing MFC project that has code that uses the MFC ribbon classes, for example, [CMFCRibbonBar Class](../mfcref/cmfcribbonbar-class.md).  
  
### To convert an MFC ribbon to a ribbon resource  
  
1.  In Visual Studio, in an existing MFC project, open the source file where the CMFCRibbonBar object is initialized. Typically, the file is mainfrm.cpp. Add the following code after the initialization code for the ribbon.  
  
    ```  
    m_wndRibbonBar.SaveToXMLFile("RibbonOutput.xml");  
    ```  
  
     Save and close the file.  
  
2.  Build and run the MFC application, and then in Notepad, open RibbonOutput.txt and copy its contents.  
  
3.  In Visual Studio, on the **Project** menu, click **Add Resource**. In the **Add Resource** dialog box, select **Ribbon** and then click **New**.  
  
     Visual Studio creates a ribbon resource and opens it in design view. The ribbon resource ID is IDR_RIBBON1, which is displayed in **Resource View**. The ribbon is defined in the ribbon1.mfcribbon-ms XML file.  
  
4.  In Visual Studio, open ribbon1.mfcribbon-ms, delete its contents, and then paste the contents of RibbonOutput.txt, which you copied earlier. Save and close ribbon1.mfcribbon-ms.  
  
5.  Again open the source file where the CMFCRibbonBar object is initialized (typically, mainfrm.cpp) and comment out the existing ribbon code. Add the following code after the code that you commented out.  
  
    ```  
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);  
    ```  
  
6.  Build the project and run the program.  
  
## See Also  
 [Ribbon Designer (MFC)](../mfc/ribbon-designer--mfc-.md)