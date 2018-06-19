---
title: 驗證設定 |Microsoft 文件
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
ms.openlocfilehash: 574e4a27342680ef4a37f6b12059cbf97bd9584a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25961956"
---
# <a name="validation-settings"></a>驗證設定
使用[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]，您可以驗證您針對 HL7 標準的訊息。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可確保您傳送或接收的訊息具有符合標準 HL7 訊息結構和內文區段。 您也可以驗證 HL7 支援自訂資料型別，並允許尾端分隔符號。 您使用[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管**驗證**索引標籤，設定驗證。  
  
## <a name="configuring-validation-settings"></a>設定驗證設定  
 您使用**驗證** 索引標籤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管 (在高階**合作對象** 索引標籤) 來設定驗證設定。 您可以選取下列類型的驗證：  
  
-   語法、 結構和內文區段，依據訊息結構描述圖解驗證  
  
-   HL7 標準驗證自訂資料類型 （DT、 TS、 TM 和曼非斯）  
  
-   欄位分隔符號 （允許尾端分隔符號） 的驗證  
  
 使用此索引標籤，您也可以設定用於此合作對象的訊息上的驗證結構描述命名空間。  
  
 下圖顯示[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管**驗證** 索引標籤。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-val.gif "hl7_ops_val")  
BTAHL7 組態總管驗證索引標籤  
  
 您可以使用下列程序來設定驗證設定。  
  
#### <a name="to-open-btahl7-configuration-explorer"></a>若要開啟 BTAHL7 組態總管  
  
-   按一下**啟動**，按一下 **程式**，按一下  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 Configuration 總管**。  
  
#### <a name="to-configure-validation-settings"></a>若要設定驗證設定  
  
1.  在 BTAHL7 組態總管，於**驗證**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**驗證主體區段**|選取此選項以執行語法、 結構和結構描述驗證。|  
    |**驗證的自訂資料類型**|選取此選項可在 DT、 TS、 TM 和曼非斯自訂資料型別上執行 HL7 標準驗證。|  
    |**允許尾端分隔符號 （分隔符號）**|選取此選項可啟用訊息執行個體中的尾端欄位分隔符號。|  
    |**結構描述命名空間**|輸入結構描述命名空間位置。 預設值是 http://microsoft.com/HealthCare/HL7/2X。|  
  
2.  按一下 **[儲存]**。  
  
## <a name="see-also"></a>請參閱  
 [記錄設定](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md)   
 [通知設定](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-settings.md)   
[作業記錄、訊息批次處理、驗證和通知設定](../../adapters-and-accelerators/accelerator-hl7/operational-logging-message-batching-validation-and-asknowledgment-settings.md)