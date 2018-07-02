---
title: A4SWIFT Message Repair 和 New Submission 的安全性功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, messages
- A4SWIFT, security
- security, A4SWIFT
- messages, security
ms.assetid: c34bcba7-fecd-4e2f-ab49-a6ccfd96198b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff2a4960d95b46ae8c224c17ff279719d51d8b37
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986039"
---
# <a name="a4swift-security-features-for-message-repair-and-new-submission"></a>A4SWIFT Message Repair 和 New Submission 的安全性功能
[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] 提供的方塊外機能 SWIFT 的訊息建立、 修復、 重設金鑰驗證及核准。 商務使用者建立、 編輯和檢閱 SWIFT 訊息所使用的 Microsoft [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]，以提供圖形化表示法和使用者介面的財務 (FIN) 訊息。 [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 從 A4SWIFT 執行階段所產生的 XML 呈現項目/修復/重設金鑰驗證表單和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 提供 A4SWIFT[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]範本針對每個 FIN 訊息 （根據對應的 A4SWIFT XSD 結構描述） 的類型，您就可以開啟在任何 SWIFT FIN 訊息類型[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]。 A4SWIFT 提供下列功能，可協助安全性。  
  
## <a name="infopath-forms"></a>InfoPath 表單  
 透過[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單產生使用 FormGenerator 公用程式所提供的 A4SWIFT，商務使用者提交擷取 SWIFT 訊息與收件匣和寄件匣上實作安全的 Windows SharePoint Services Web 資料夾。 [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)] Web 資料夾安全性由 Microsoft 提供完全[!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)]使用檔案系統存取控制清單 (Acl)、[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]驗證，以及 Internet Information Services (IIS) 安全性功能。 資料會受到保護，同時 「 在線上 」 之間[!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)]Web 資料夾和[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]Secure Sockets Layer (SSL) 和 HTTPS 傳輸通訊協定。  
  
 A4SWIFT[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單會建立為 「 不受信任。 」 此狀態會提供最高層級的安全性。 如需有關受信任和未受信任的詳細資訊，請參閱 < [InfoPath 安全性](../../adapters-and-accelerators/accelerator-swift/infopath-security.md)。  
  
## <a name="runtime-service"></a>執行階段服務  
 A4SWIFT 提供執行階段 （實作為 BizTalk 協調流程） 的服務進行驗證，驗證、 處理和路由之間的 SharePoint Web 資料夾、 訊息修復/進入協調流程、 後端系統，乃至於至 SWIFT 的 SWIFT 訊息網路。 此執行階段服務稱為 A4SWIFT Message Repair 和 New Submission。  
  
## <a name="secure-messages"></a>安全的訊息  
 儲存體和傳遞 SWIFT 的訊息之間[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]， [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)]，和 Message Repair 和 New Submission 受到基礎服務 ([!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)]，IIS， [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]) 和傳輸通訊協定 （SSL，HTTPS）。 不過，訊息的建立、 修復、 核准及提交基礎結構所組成的訊息修復和新送出， [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)]，和[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]需要額外的使用者層級安全性，以強制執行的真實性和 SWIFT 訊息保護由終端使用者。  
  
 A4SWIFT 也定義和實作使用者層級安全性的語意，以確定 SWIFT 訊息所修改，並提交只能由受信任且經過授權的使用者，而且未更改或非同步提交的步驟期間竄改訊息資料處理 （例如，當訊息坐在等候使用者介入的 SharePoint Web 資料夾）。 協調及經過工作站上的安全性功能 (透過[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]) 和伺服器 （透過 A4SWIFT Message Repair 和 New Submission） 強制執行這些使用者層級安全性原則。