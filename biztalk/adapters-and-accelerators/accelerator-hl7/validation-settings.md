---
title: 驗證設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- validating, configuring
- configuring, validating
ms.assetid: ee08acac-99f9-4403-b2ae-01b80378aa58
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01f85c02434f8b20124258d95fd484c79809b509
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966319"
---
# <a name="validation-settings"></a>驗證設定
使用[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]，您可以驗證您對 HL7 標準的訊息。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 可確保您傳送或接收的訊息具有符合標準 HL7 訊息結構和內文區段。 您也可以驗證 HL7 支援自訂資料類型，並允許尾端分隔符號。 您使用[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管**驗證**索引標籤來設定驗證。  

## <a name="configuring-validation-settings"></a>設定驗證設定  
 您使用**驗證**索引標籤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管 (底下的高階**合作對象** 索引標籤) 來設定驗證設定。 您可以選取下列類型的驗證：  

- 語法、 結構和圖解主體區段，依據訊息結構描述驗證  

- HL7 標準驗證自訂資料類型 （DT、 TS、 TM 和 TN）  

- 欄位分隔符號 （允許尾端分隔符號） 的驗證  

  使用此索引標籤，您也可以設定用於此合作對象的訊息上的驗證結構描述命名空間。  

  下圖顯示[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管**驗證** 索引標籤。  

  ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-val.gif "hl7_ops_val")  
  BTAHL7 設定總管驗證索引標籤  

  您可以使用下列程序來設定驗證設定。  

#### <a name="to-open-btahl7-configuration-explorer"></a>若要開啟 BTAHL7 設定總管  

-   按一下 **開始**，按一下**程式**，按一下  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 設定總管**。  

#### <a name="to-configure-validation-settings"></a>若要設定驗證設定  

1. 在 BTAHL7 設定總管中於**驗證**索引標籤上，執行下列動作：  


   |                  使用                  |                                            以進行此動作                                            |
   |--------------------------------------------|--------------------------------------------------------------------------------------------------|
   |         **驗證主體區段**         |             選取此選項可執行的語法、 結構和結構描述驗證。              |
   |       **驗證自訂資料類型**        |  選取此選項可 HL7 標準驗證對 DT、 TS、 TM 和 TN 自訂資料型別。  |
   | **允許尾端分隔符號 （分隔符號）** |           選取此選項可啟用在訊息執行個體中的尾端欄位分隔符號。           |
   |            **結構描述命名空間**            | 輸入結構描述命名空間位置。 預設值是 http://microsoft.com/HealthCare/HL7/2X。 |


2. 按一下 **[儲存]**。  

## <a name="see-also"></a>另請參閱  
 [記錄組態](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md)   
 [通知設定](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-settings.md)   
[作業記錄、訊息批次處理、驗證和通知設定](../../adapters-and-accelerators/accelerator-hl7/operational-logging-message-batching-validation-and-asknowledgment-settings.md)