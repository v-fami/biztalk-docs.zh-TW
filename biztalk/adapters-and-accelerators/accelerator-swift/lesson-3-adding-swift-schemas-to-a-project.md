---
title: 第 3 課： 將 SWIFT 結構描述加入專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- schemas, adding to projects
- projects
ms.assetid: e17ef4b8-f060-44cc-b988-0f9f54deab90
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3fcaa7f9af0dd802f457f84d7661f92bcdf08157
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982039"
---
# <a name="lesson-3-adding-swift-schemas-to-a-project"></a>第 3 課： 將 SWIFT 結構描述加入至專案
既然您有方案和新的專案，您可以在專案中加入項目。 您新增的第一個項目是 MT103 SWIFT 付款訊息結構描述。 當您選取的結構描述範本時，BizTalk 編輯器會啟動。  
  
### <a name="to-add-a-new-schema-to-the-project"></a>新增新結構描述至專案  
  
1. 在 [方案總管] 中，以滑鼠右鍵按一下**SWIFTSchemas**專案，指向**新增**，然後按一下**現有項目**。  
  
2. 在 [加入現有項目-SWIFTSchemas] 對話方塊中，瀏覽至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本\>MessagePack\SWIFT Messages\A4SWIFT SRG\<版本\>\Base 結構描述**。  
  
3. 選取  **SWIFT 基底 Types.xsd**並**SWIFT 常見資料 Types.xsd**結構描述，然後再按一下**新增**。  
  
   > [!NOTE]
   >  SWIFT 基底 Types.xsd 和通用資料 Types.xsd SWIFT 結構描述會出現在 方案總管 SWIFTSchemas 專案底下。  
  
4. 在 [方案總管] 中，以滑鼠右鍵按一下**SWIFTSchemas**專案，指向**新增**，然後按一下**現有項目**。  
  
5. 在 [加入現有項目-SWIFTSchemas] 對話方塊中，瀏覽至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本\>MessagePack\SWIFT Messages\A4SWIFT SRG\<版本\>\Category 1\MT103**資料夾。  
  
6. 選取  **MT103.xsd**結構描述，然後再按一下**新增**。  
  
   > [!NOTE]
   >  新的結構描述，MT103.xsd，會出現在 [方案總管] 中，SWIFTSchemas 專案之下。  
  
7. 在 [方案總管] 中，按兩下**MT103.xsd**若要在 [BizTalk 編輯器] 中檢視結構描述。  
  
   > [!NOTE]
   >  XSD 檢視 （右窗格） 與結構描述樹狀結構 （左窗格） 會出現在 「 BizTalk 編輯器 」 中。  
  
8. 在上**檔案**功能表上，按一下**全部儲存**以儲存變更。  
  
   請繼續進行[第 4 課： 建置和部署組件](../../adapters-and-accelerators/accelerator-swift/lesson-4-building-and-deploying-the-assembly.md)。