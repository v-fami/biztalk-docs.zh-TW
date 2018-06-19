---
title: 步驟 1： 參考結構描述 DLL1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47e4b773-e484-4931-9ab2-b8dd0080ea1c
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9c2d5051c7dfd3c0f971b34922ca4e5747117c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279438"
---
# <a name="step-1-reference-the-schema-dll"></a>步驟 1： 參考結構描述 DLL
在 BizTalk 中，訊息都是不變的。 因此，若要變更屬性值，您必須建立新訊息並加以修改。 在接收和傳送圖形之間插入訊息指派圖形，就可以建立新訊息和加以修改。  
  
 但首先您必須先參考結構描述 DLL，才能取得 J.D. Edwards EnterpriseOne 內容屬性的存取權。  
  
### <a name="to-reference-the-schema-dll"></a>若要參考結構描述 DLL  
  
1.  建立專案的工作資料夾，例如 c:\class\JDE\BeginDoc，以及要置放測試 XML 的資料夾，例如 c:\class\JDE\input。  
  
2.  建立靜態請求-回應傳送埠傳送要求給 J.D. Edwards EnterpriseOne。  
  
     ![JDOneWorld 傳輸屬性](../core/media/example-2waysendport-ow.gif "example_2waysendport_OW")  
  
3.  在方案編輯器中，使用滑鼠右鍵按一下專案。  
  
    1.  選取**新增**，選取**新增產生的項目**，然後按一下 **新增配接器**。  
  
    2.  選取 Microsoft BizTalk Adapter for J.D. Edwards EnterpriseOne 以及您剛才建立的連接埠。  
  
    3.  在**新增配接器精靈**，選取 **[csales\b4200310]**。  
  
    4.  按一下**完成**產生結構描述包含訊息的格式。  
  
     ![新增配接器精靈](../core/media/add-adapter-wizard.gif "add_adapter_wizard")  
  
4.  在 Visual Studio 中，開啟 [方案總管]。  
  
5.  以滑鼠右鍵按一下**參考**，然後選取**加入參考**。  
  
6.  在**加入參考**畫面上，按一下**瀏覽** 按鈕。  
  
7.  在**選取元件**畫面上，瀏覽至 %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin。  
  
8.  選取**microsoft.adapters.jdeproperties.dll**，然後按一下 **開啟**。  
  
9. 在**加入參考** 畫面上，此 DLL 會出現在**選取的元件**> 一節。  
  
     ![屬性選取畫面](../core/media/properties-selection.gif "properties_selection")  
  
10. 按一下 **[確定]**。  
  
11. 按兩下協調流程來存取協調流程設計師。  
  
     \- 或 -  
  
     選取**檢視**，選取**其他視窗**，然後按一下 **協調流程檢視**。  
  
     [協調流程檢視] 隨即出現。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 2： 建立協調流程](../core/step-2-create-the-orchestration2.md)   
 [工作 4： 設定建構訊息圖形](../core/task-4-configure-the-construct-message-shape1.md)   
 [工作 5： 設定轉換圖形](../core/task-5-configure-the-transform-shape2.md)   
 [步驟 3： 完成及執行專案](../core/step-3-complete-and-run-the-project1.md)   
 [步驟 4： 建立範例 XML BeginDoc](../core/step-4-create-a-sample-xml-begindoc2.md)