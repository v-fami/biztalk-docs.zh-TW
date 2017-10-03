---
title: "疑難排解 BizTalk ESB 工具組 |Microsoft 文件"
description: "疑難排解安裝問題，以及在 BizTalk Server ESB Toolkit 的常見錯誤"
caps.latest.revision: "2"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1ea2d56-2ace-40f2-80df-8a7489bbfc2e
ms.author: mandia
ms.openlocfilehash: 8fc1305e481de2444a54ea994f8a53da83b2eaed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-the-biztalk-esb-toolkit"></a>疑難排解 BizTalk ESB 工具組

  
## <a name="installation"></a>安裝  
  
|問題|解決方案|  
|-----------|----------------|  
|您會收到在安裝期間指派的權限的 「 錯誤 」 例外狀況。|[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]使用標準的 BizTalk 帳戶群組，必須在安裝程序或在安裝期間將會失敗。 此外，此工具組會假設電腦所在的工作群組成員的獨立安裝或企業安裝電腦所在網域的成員。|  
|應用程式匯入失敗並出現錯誤訊息，警告信任層級不相符。|Microsoft.BizTalk.ESB 繫結檔案會設定為使用預設 BizTalkServerApplication 與 BizTalkServerIsolatedHost，接著會設定為在不受信任模式下執行。 如果您已變更您的主機在信任模式下執行，將不會匯入繫結檔案。 若要修正此問題，您必須將信任層級變更為不受信任，或編輯繫結檔案，以符合您的環境中 BizTalk Toolkit \Bindings 目錄。|  
|網際網路資訊服務 (IIS) 中未設定 Kerberos 驗證。|若要啟用 IIS 的 Kerberos 驗證，請參閱 Microsoft 知識庫中的下列文章：<br /><br /> -   [如何設定 IIS 以支援用於網路驗證的 Kerberos 通訊協定與 NTLM 通訊協定](http://go.microsoft.com/fwlink/?LinkId=188566)<br />-   [如何啟用 IIS 的電腦不是網域控制站上使用 Kerberos 驗證](http://go.microsoft.com/fwlink/?LinkId=188567)<br />-   [您無法設定的交涉或 NTLM 通訊協定 Windows 整合式驗證 IIS 管理員中的網際網路資訊服務 (IIS) 7.0](http://go.microsoft.com/fwlink/?LinkId=188568)|  
  
## <a name="general-issues"></a>一般問題  
  
|問題|解決方案|  
|-----------|----------------|  
|將訊息傳送至泛型 ESB 行程上手 Web 服務時，您會收到 「 內部 SOAP 處理 」 的例外狀況。|使用 BizTalk Server 管理主控台確認 Microsoft.Practices.ESB 應用程式正在執行。如果未執行，，啟動它。|  
|ESB 管理入口網站中沒有出現例外狀況訊息。|請檢查 [BizTalk 系統管理員群組概觀] 頁面和 Windows 應用程式事件記錄檔，表示傳送訊息失敗的項目。 您可能需要重新傳送配接器 （Microsoft.Practices.ESB 應用程式的一部分） 的例外狀況設定以符合您的環境。 此外，請注意 BizTalk 失敗訊息路由的功能和 BizTalk ESB Toolkit 例外狀況管理架構產生的例外狀況訊息。 因此，請確定您啟用**失敗訊息路由，**選項傳送和接收埠。|  
|當具有靜態解析程式使用 WCF 服務，您會收到 「 無效的 SOAP 動作例外狀況。|如果 WCF 服務的 SOAP 動作不包括目標命名空間，設定的 SOAP 動作值解析程式設定中使用下列格式: {action} 指示的目標命名空間不串連 ESB Toolkit 核心引擎在執行階段。|