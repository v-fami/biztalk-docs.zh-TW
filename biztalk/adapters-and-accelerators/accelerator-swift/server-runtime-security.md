---
title: 伺服器執行階段安全性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, server runtime
- servers, security
- servers, runtime
ms.assetid: 40f5ca3e-d9d3-4543-bd38-82283c343b76
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c690c6e34e5ac8d5f70bc58cfd36e4e99006e8b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976263"
---
# <a name="server-runtime-security"></a>伺服器執行階段安全性
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Message Repair 和 New Submission 控制 SWIFT 的訊息，商務使用者、 後端系統和 SWIFT 網路端點之間的流量安全且具決定性的方式。 它會驗證商務使用者所提交的訊息、 驗證訊息的資料和商務規則的正確性，並將訊息路由傳送到後端系統或最終傳遞至 SWIFT 的網路。 如需有關數位簽章的詳細資訊，請查看 [加密及簽署憑證] 上 MSDN 文件庫網站，在[ http://go.microsoft.com/fwlink/?linkid=50285 ](http://go.microsoft.com/fwlink/?linkid=50285)。  
  
 Message Repair 和 New Submission[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]協調流程應用程式，裝載，而且執行[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安全性內容。 它會保護，當做[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]稍早所述的安全性功能。 Message Repair 和 New Submission 也定義並強制執行特定的 SWIFT 的訊息建立、 修復、 核准及提交的使用者層級安全性原則，如下所示：  
  
- 全新或修復，所有訊息都提交至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]透過 Message Repair 和 New Submission 必須來自受信任的使用者。  
  
- 建立或修復訊息的受信任的使用者必須具有正確的授權和權限。 核准或拒絕訊息的受信任的使用者必須具有正確的授權和權限。  
  
- 所有訊息必須經過已知數目的受信任的使用者都核准。 必須是唯一的訊息建立者、 repairer，以及核准者鏈結中每個信任的使用者，相同的使用者無法建立或修復以及核准或拒絕訊息。 相同的使用者無法輸入多個核准或拒絕決策中包含多個步驟的核准程序的單一訊息。 您無法核准您自己建立或修復的訊息，也不可以核准多個核准者為相同的訊息。  
  
- 您無法改變一則訊息，在核准程序期間 （也就是訊息無法在之後修改原始送交 Message Repair 和 New Submission，為全新或修復的訊息）。  
  
- 重設金鑰驗證階段期間變更的訊息必須完全符合原始訊息 （建立或修復）。  
  
  若要強制這些安全性語意，訊息修復和新送出驗證內嵌在每個收到，建立或修復核准提交程序的每個階段的 XML 訊息的數位簽章。 Message Repair 和 New Submission 的數位簽章驗證可執行下列檢查。 如果一或多個這些檢查會失敗，Message Repair 和 New Submission 的停駐點，而且會儲存到訊息方塊中，並將安全性錯誤會記錄在事件記錄檔中：  
  
- XML 訊息必須經過數位簽署，因此必須包含對應的數位簽章。  
  
- 每個工作流程中使用的數位簽章必須設定為使用受信任的數位憑證。 這可確保訊息建立者、 repairer、 驗證器和核准者是受信任。  
  
- 每個受信任的數位認證必須屬於[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]網域，使用者是否具有邏輯的授權單位或內執行動作的權限的網域群組成員資格[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。 這可確保在建立或送出核准修復動作的程序中的每個參與者都具有正確的授權或權限來執行它們執行的特定動作。  
  
   上述規則會強制執行透過 SharePoint 網站，透過網站使用者群組和表單送出程式碼上的 Acl。 若訊息執行位置的使用者不是處於[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者群組 （網域或本機） Message Repair 和 New Submission 會拒絕訊息。  
  
   例如，組織強制執行的三階段的核准程序可能會定義這三個邏輯角色： Repairers、 驗證者 （重設金鑰階段） 和核准者。 同樣地，參與角色的使用者必須屬於[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者網域群組。 進一步鎖定 SharePoint 網站的使用者應該會組織成邏輯網域群組 （例如 repairers，驗證者，核准者）。  
  
   如需站台的使用者群組的詳細資訊，請參閱[Windows SharePoint Services 安全性](../../adapters-and-accelerators/accelerator-swift/windows-sharepoint-services-security.md)。  
  
- 每個堆疊中的數位簽章必須是唯一的。 也就是說，每個數位簽章必須設定為使用唯一的數位憑證 （相對於其他的簽章相同堆疊中）。 這可確保訊息，未經核准所建立/修復訊息的人員，且完全沒有人核准為多位核准者相同的訊息。  
  
  Message Repair 和 New Submission 會施加嚴格的安全性原則，讓檢查點的訊息建立、 修復、 核准及提交基礎結構每個進入點。 這些檢查點會緊密結合的 Message Repair 和 New Submission 的核心功能，因此無法規避。 雖然 Message Repair 和 New Submission 的設計為緊密整合[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形式簽署功能，它也設計為安全且穩健地強制執行的真實性和 SWIFT 的訊息，即使保護而[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]是不使用訊息會直接由結束使用者提交到 Message Repair 和 New Submission 接收結束點 （SharePoint Web 資料夾）。