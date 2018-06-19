---
title: 企業單一登入概觀 |Microsoft 文件
description: 閱讀有關 affilicate 應用程式，在 BizTalk Server 中使用以處理訊息，以及 adminster SSO 的 SSO 票證
ms.custom: ''
ms.date: 10/11/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2aaab59-8cf7-4848-b71a-e7c8682dd3bd
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f242e11e31de957fee0c6cbf228094f7e40010d
ms.sourcegitcommit: 5e6ef63416e8885a5ee91bd65618a842b3a0cc54
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2017
ms.locfileid: "23129695"
---
# <a name="enterprise-single-sign-on-overview"></a>企業單一登入概觀
依賴多個不同應用程式的商務程序可能必須跨多個不同的安全性網域。 存取 Microsoft Windows 系統上的應用程式可能需要一組安全性認證，而存取 IBM 大型主機的應用程式可能需要不同的認證，如 RACF 使用者名稱及密碼。 使用者要處理這麼大量的認證十分不易，而且對於自動化程序會造成更大的難題。 若要解決這個問題，請[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]包含企業單一登入。  
  
 不會混淆 — 這不是一套機制，可讓人擁有的所有應用程式的單一登入。 而是「企業單一登入」提供一種方法，可以將 Windows 使用者識別碼對應至非 Windows 使用者認證。 它不會解決所有組織的企業單一登入問題，但這項服務可以讓不同系統上使用應用程式的商務程序較為簡化。  
  
## <a name="create-affiliate-application-for-non-windows-systems"></a>建立非 Windows 系統的分支機構應用程式  
 若要使用「企業單一登入」，系統管理員要定義分支機構應用程式，其中的每一個都代表非 Windows 系統或應用程式。 例如，分支機構應用程式可以是在 IBM 大型主機上執行的 CICS 應用程式、在 Unix 上執行的 SAP ERP 系統，或任何其他類型的軟體。 這些應用程式每一個都有自己的驗證機制，因此每一個都需要自己特有的認證。  
  
 「企業單一登入」會在 SSO 資料庫中，儲存使用者的 Windows 使用者識別碼與其針對一或多個分支機構應用程式所擁有認證之間的對應。 當此使用者需要存取某個分支機構應用程式時，單一登入 (SSO) 伺服器就會在 SSO 資料庫中查詢該應用程式的認證。 下圖顯示作業方式。  
  
 ![](../core/media/understandingbts-11-esso.gif "UnderstandingBTS_11_ESSO")  
  
 在此範例中，部分應用程式傳送至 BizTalk Server 的訊息是由協調流程處理的，然後傳送至在 IBM 大型主機上執行的分支機構應用程式。 「企業單一登入」的工作是確定正確的認證 (也就是正確的使用者名稱和密碼) 在訊息傳送至分支機構應用程式時會一併傳送。  
  
## <a name="message-processing-with-an-sso-ticket"></a>使用 SSO 票證的訊息處理  
 如圖所示，當接收配接器取得訊息時，配接器可從 SSO 伺服器 A (步驟 1) 要求 SSO 票證。 這個加密票證包含發出要求及逾時之使用者的 Windows 識別。 (不要與 Kerberos 票證混淆這個 — 這不是相同的動作。)取得票證之後，票證會當成屬性新增至內送訊息。 訊息接下來會透過 BizTalk Server 引擎取得正常路徑，在此範例中表示由協調流程處理。 當此協調流程產生外寄訊息，訊息也會包含先前取得的 SSO 票證。  
  
 此新訊息是傳送至在 IBM 大型主機執行的應用程式，而且它必須包含該使用者的適當認證，才能存取該應用程式。 若要取得這些認證，傳送配接器會連繫 SSO 伺服器 B (步驟 2)，提供剛收到的訊息 (包含 SSO 票證) 以及分支機構應用程式的名稱 (為其接收認證)。 此作業稱為贖回 (Redemption)，會使得 SSO 伺服器 B 驗證 SSO 票證，然後為應用程式查詢此使用者的認證 (步驟 3)。 SSO 伺服器 B 會將這些認證傳回傳送配接器 (步驟 4)，該步驟使用這些認證將適當的驗證訊息傳送到分支機構應用程式 (步驟 5)。  
  
## <a name="administering-sso"></a>管理 SSO  
 「企業單一登入」還包括可執行各種作業的管理工具。 在 SSO 資料庫上執行的所有作業都會接受稽核；例如，系統管理員可使用提供的工具，監視這些作業以及設定不同的稽核層次。 系統管理員還可使用其他工具停用特定的分支機構應用程式、開啟和關閉使用者的個別對應，以及執行其他功能。 還有一個用戶端公用程式，可以讓一般用者設定自己的認證和對應。 和 BizTalk Server 的其他部分一樣，「企業單一登入」透過可設計程式的 API 公開它的服務。 協力廠商 BizTalk Server 配接器的建立者使用此 API 存取單一登入服務，而系統管理員也可以用它來建立指令碼，將日常工作自動化。  
  
 上述範例顯示「企業單一登入」的一般用法，但是您也可以使用其他方法來設定 SSO。 例如，小型的 BizTalk Server 安裝可能只有一個 SSO 伺服器，可以從 BizTalk Server 引擎獨立使用「企業單一登入」。 (這項技術也隨附於 Microsoft Host Integration Server)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 傳訊引擎](../core/the-biztalk-server-messaging-engine.md)   
 [實作企業單一登入](../core/implementing-enterprise-single-sign-on.md)
