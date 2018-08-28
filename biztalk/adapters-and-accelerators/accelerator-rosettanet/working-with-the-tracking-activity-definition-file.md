---
title: 使用追蹤活動定義檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tracking, activity definition file
- activity definition file
- activity definition file, about activity definition file
- tracking, managing views
- activity definition file, activity fields
ms.assetid: 0592a844-aad7-4054-b1e7-344f1086f0b1
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0be795daa7e08707c113d8230dc8d324bc71f951
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991911"
---
# <a name="working-with-the-tracking-activity-definition-file"></a>使用追蹤活動定義檔案
活動定義檔案包含追蹤資訊 Microsoft® 中的程序和訊息活動[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 您可以使用這個檔案來管理資料追蹤的 BizTalk 商務活動監控 (BAM)。 定義檔案是 XML 檔案 (Tracking.xml)，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]安裝程式會安裝\<*磁碟機*\>: \Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet \BAMTracking 資料夾。 Tracking.xml 中定義的活動對於您的目的而言應該很足夠了。  
  
 如需追蹤活動、 檢視和資料表的詳細資訊，請參閱[增強型追蹤](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md)。 如需有關 BAM 的詳細資訊，請參閱 「 商務活動監控 (BAM) 」 在 BizTalk Server 說明中。  
  
## <a name="managing-tracking-views"></a>管理追蹤檢視  
 請勿將 BizTalk「追蹤設定檔編輯器」與 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 追蹤一起使用。 追蹤點無法自訂；請勿變更活動定義。 不過，您可以管理 BAM 檢視與部署， 若要這樣做，您修改[!INCLUDE[btsExcel](../../includes/btsexcel-md.md)]試算表 (Tracking.xls)，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]安裝程式會安裝\<*磁碟機*\>: \Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\BAMTracking 資料夾中。 如需詳細資訊，請參閱下列的＜管理追蹤檢視＞。  
  
 如果 Tracking.xml 中定義的檢視還無法滿足您的需求，您也可以依照以下的方式定義對 BAM 中所追蹤資訊的其他檢視。  
  
#### <a name="to-create-different-tracking-views"></a>建立不同的追蹤檢視  
  
1. 按一下 **[開始]**，然後按一下 **[執行]**。 請輸入**cmd**在開啟的文字方塊中，然後按一下 [執行] 對話方塊中，以及**確定**。 在命令列] 對話方塊中，輸入下列程式碼以解除部署 tracking.xml，然後按一下 [**確定**:  
  
   ```  
   cd %ProgramFiles%\Microsoft BizTalk Server 2013\Tracking  
   bm remove-all  -DefinitionFile:"%ProgramFiles%\Microsoft BizTalk 2013 Accelerator for RosettaNet\BAMTracking\<filename\>.xml"  
   ```  
  
2. 在 [[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管] 中，移至*\<磁碟機\>*: \Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet \BAM 追蹤。 按兩下 Tracking.xls。  
  
3. 在 [商務活動監控] 中建立一個新的檢視。 如需如何執行這項操作的資訊，請參閱 < 管理商務活動監控 」 在 BizTalk Server 說明中。  
  
4. 按一下  **BAM**，然後按一下**匯出 XML**。 移至想要的位置，輸入檔案名稱 （不可以是 Tracking.xml)，然後按一下 **儲存**。  
  
   > [!IMPORTANT]
   >  當您在追蹤 XLS 檔案內定義了新的追蹤檢視，並且將此追蹤 XLS 檔案匯出成 XML 檔案時，某些新的欄位名稱可能會稍微有點修改。 請把您自訂的追蹤 XML 檔案中的這些欄位和 BTARN 安裝程式安裝的標準 tracking.xml 欄位比對，就可以找出並予以更正。  
  
5. 部署新的追蹤 XML 檔案。 若要這樣做，請按一下**開始**，然後按一下**執行**。 請輸入**cmd**在開啟的文字方塊中，然後按一下 [執行] 對話方塊中，以及**確定**。 在命令列] 對話方塊中，輸入下列程式碼，以部署新的追蹤檔案，然後按一下 [**確定**。 建議您最好修改此追蹤 XML 檔案的名稱，以免覆寫預設的 tracking.xml 檔案。  
  
   ```  
   cd %ProgramFiles%\Microsoft BizTalk Server 2013\Tracking  
   bm.exe deploy-all -DefinitionFile:"%ProgramFiles%\Microsoft BizTalk 2030 Accelerator for RosettaNet\BAMTracking\<filename\>.xml"  
   ```  
  
   BAM 中追蹤的資訊不包含訊息內容，因為訊息內容存放在 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 資料庫。  
  
   您可以使用「商務活動監控管理公用程式」來管理 BAM 追蹤的部署。 如需有關此公用程式的詳細資訊，請參閱 「 使用商務活動監控管理公用程式 」 在 BizTalk Server 說明中。  
  
## <a name="activity-fields"></a>活動欄位  
 以下為活動定義檔案中，訊息活動的欄位：  
  
- ActivityName  
  
- 類別目錄  
  
- ContentKey  
  
- DestinationPartyName  
  
- ErrorDescription  
  
- HasError  
  
- InReplyToMessageID  
  
- IsReceived  
  
- MessageTrackingID  
  
- NoFPipInstance  
  
- PipCode  
  
- PipInstanceID  
  
- PiPVersion  
  
- SourcePartName  
  
- 時間戳記  
  
  以下為活動定義檔案中，程序活動的欄位：  
  
- EndTime  
  
- InitiatorPartyName  
  
- IsInitiatorRole  
  
- PipCode  
  
- PipInstanceID  
  
- PipName  
  
- PipVersion  
  
- ResponderPartyName  
  
- StartTime  
  
- [狀態]  
  
## <a name="see-also"></a>另請參閱  
 [加強的追蹤](../../adapters-and-accelerators/accelerator-rosettanet/enhanced-tracking.md)   
 [管理設定、憑證、資料庫和安全性](manage-configuration-certificates-databases-security.md)