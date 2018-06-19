---
title: 步驟 1： 參考結構描述 DLL2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1db92227-6164-42b9-b60c-12dd2cae46e2
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5b009e2c79c0ea68030561c51e3a90ceef24eba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277526"
---
# <a name="step-1-reference-the-schema-dll"></a>步驟 1： 參考結構描述 DLL
在 BizTalk 中，訊息都是不變的。 因此，若要變更屬性值，您必須建立新訊息並加以修改。 在接收和傳送圖形之間插入訊息指派圖形，就可以建立新訊息和加以修改。  
  
 但首先您必須先參考結構描述 DLL，才能取得 J.D. Edwards 內容屬性。  
  
### <a name="to-reference-the-schema-dll"></a>若要參考結構描述 DLL  
  
1.  建立專案的工作資料夾，例如 c:\class\JDE\BeginDoc，以及要置放測試 XML 的資料夾，例如 c:\class\JDE\input。  
  
2.  建立靜態請求-回應傳送埠傳送要求給 J.D. Edwards OneWorld。  
  
     ![](../core/media/jde-example-2waysendport-ow.gif "JDE_example_2waysendport_OW")  
  
3.  在方案編輯器中，使用滑鼠右鍵按一下專案。  
  
    1.  選取**新增**，選取**新增產生的項目**，然後按一下 **新增配接器**。  
  
    2.  選取 Microsoft BizTalk Adapter for J.D. Edwards OneWorld 和您剛建立的連接埠。  
  
    3.  在**新增配接器精靈**，選取 **[csales\b4200310]**。  
  
    4.  按一下**完成**產生結構描述包含訊息的格式。  
  
     ![](../core/media/jde-add-adapter-wizard.gif "JDE_add_adapter_wizard")  
  
4.  在 Visual Studio 中，開啟 [方案總管]。  
  
5.  以滑鼠右鍵按一下**參考**，然後選取**加入參考**。  
  
6.  在**加入參考**畫面上，按一下**瀏覽** 按鈕。  
  
     ![](../core/media/jde-add-reference-dll.gif "JDE_add_reference_dll")  
  
7.  在**選取元件**畫面上，瀏覽至 %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin。  
  
8.  選取**microsoft.adapters.jdeproperties.dll**，然後按一下 **開啟**。  
  
9. 在**加入參考** 畫面上，此 DLL 會出現在**選取的元件**> 一節。  
  
     ![](../core/media/jde-properties-selection.gif "JDE_properties_selection")  
  
10. 按一下 **[確定]**。  
  
11. 按兩下協調流程來存取協調流程設計師。  
  
     \- 或 -  
  
     選取**檢視**，選取**其他視窗**，然後按一下 **協調流程檢視**。  
  
     [協調流程檢視] 隨即出現。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 2： 建立協調流程](../core/step-2-create-the-orchestration1.md)   
 [步驟 3： 完成及執行專案](../core/step-3-complete-and-run-the-project2.md)   
 [步驟 4： 建立範例 XML BeginDoc](../core/step-4-create-a-sample-xml-begindoc1.md)