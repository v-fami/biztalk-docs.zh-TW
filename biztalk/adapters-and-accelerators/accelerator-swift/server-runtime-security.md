---
title: 伺服器執行階段安全性 |Microsoft 文件
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
ms.openlocfilehash: 9a5979162a521185b87977191c9d709fb754b1ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214126"
---
# <a name="server-runtime-security"></a>伺服器執行階段安全性
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]Message Repair 和 New Submission 控管 SWIFT 訊息商務使用者、 後端系統和 SWIFT 網路端點之間的流量以安全且具有決定性的方式。 它會驗證商務使用者所提交的訊息，會驗證訊息的資料和商務規則正確，並將訊息路由傳送至後端系統或最終傳遞到 SWIFT 網路。 多個數位簽章的詳細資訊，請參閱 < 加密和簽署憑證 >，MSDN Library 網站上[http://go.microsoft.com/fwlink/?linkid=50285](http://go.microsoft.com/fwlink/?linkid=50285)。  
  
 Message Repair 和 New Submission 是[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]協調流程應用程式、 裝載和執行在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安全性內容。 它會保護，當做[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]稍早所述的安全性功能。 Message Repair 和 New Submission 也會定義並強制執行特定的 SWIFT 訊息建立、 修復、 核准，以及提交的使用者層級安全性原則，如下所示：  
  
-   全新或修復，所有訊息都提交給[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]透過 Message Repair 和 New Submission 必須來自受信任的使用者。  
  
-   受信任的使用者建立或修復訊息之人員必須將正確的授權和權限。 核准或拒絕訊息的受信任的使用者必須擁有正確的授權和權限。  
  
-   所有訊息都必須都核准依已知的信任的使用者數目。 必須是唯一的訊息建立者、 repairer 和核准者鏈結中每個信任的使用者，相同的使用者無法建立或修復並核准或拒絕訊息。 相同的使用者無法輸入多個核准或拒絕決策中包含多個步驟的核准程序的單一訊息。 您無法核准您自己建立或修復的訊息，也不可以核准做為多個核准者相同的訊息。  
  
-   核准程序期間，您無法改變一則訊息 （亦即，訊息無法改變原始送出訊息修復和新送出，做為全新或修復的訊息之後）。  
  
-   重設金鑰驗證階段期間所改變的訊息必須完全符合原始訊息 （建立或修復）。  
  
 若要強制這些安全性語意，訊息修復和新送出驗證內嵌在收到，在建立或修復核准提交程序的每個階段中每個 XML 訊息的數位簽章。 Message Repair 和 New Submission 的數位簽章驗證可執行下列檢查。 如果一或多個這些檢查會失敗，訊息修復和新送出停駐點和保存透過訊息方塊中和安全性錯誤會記錄在事件記錄檔：  
  
-   XML 訊息必須經過數位簽署，因此必須包含對應的數位簽章。  
  
-   每個工作流程中使用的數位簽章必須所使用的受信任的數位憑證。 這可確保訊息的建立者、 repairer、 驗證器和核准者信任。  
  
-   每個受信任的數位認證必須屬於[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]是否具有邏輯授權單位或內執行動作的權限的網域群組成員資格的網域使用者[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。 這可確保在建立或送出核准修復動作的程序中的每個參與者都有正確的授權或權限可執行所執行的特定動作。  
  
     在前述規則會強制執行透過網站使用者群組和表單送出程式碼在 SharePoint 網站上的 Acl。 如果訊息時所做的使用者不是在[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]Users 群組 （網域或本機） Message Repair 和 New Submission 會拒絕訊息。  
  
     例如，組織強制執行的三階段核准程序可能會定義這三個邏輯角色： Repairers、 能力檢查器 （重設金鑰階段） 和核准者。 相對的參與角色的使用者必須屬於[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者網域群組。 SharePoint 網站的進一步鎖定使用者應該會組織成邏輯網域群組 （例如 repairers、 能力檢查器、 核准者）。  
  
     如需有關網站使用者群組，請參閱[Windows SharePoint Services 安全性](../../adapters-and-accelerators/accelerator-swift/windows-sharepoint-services-security.md)。  
  
-   每個堆疊中的數位簽章必須是唯一的。 也就是說，每個數位簽章必須進行使用唯一的數位認證 （相對於其他的簽章相同的堆疊中）。 這可確保訊息的建立/修復訊息的人員所未獲核准並沒有人核准做為多個核准者相同的訊息。  
  
 Message Repair 和 New Submission 設有嚴格的安全性原則需要在每個訊息建立、 修復、 核准，以及提交基礎結構的進入點的檢查點。 這些檢查點緊密結合的訊息修復和新送出的核心功能，因此無法受到危害。 雖然 Message Repair 和 New Submission 旨在緊密整合[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單簽署功能，它也設計為安全、 強固程度足以強制執行驗證和保護 SWIFT 的訊息，即使[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]是不使用訊息送出直接的使用者訊息修復和新送出接收結束點 （SharePoint Web 資料夾）。