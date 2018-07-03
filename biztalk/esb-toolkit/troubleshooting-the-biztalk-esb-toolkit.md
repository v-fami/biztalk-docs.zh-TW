---
title: 疑難排解 BizTalk ESB 工具組 |Microsoft Docs
description: 針對安裝問題和使用 ESB 工具組，在 BizTalk Server 中的常見錯誤進行疑難排解
caps.latest.revision: 2
author: MandiOhlinger
manager: anneta
ms.custom: ''
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1ea2d56-2ace-40f2-80df-8a7489bbfc2e
ms.author: mandia
ms.openlocfilehash: 5dc6c935933d9879005bafc75bb993f7d436ef50
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992543"
---
# <a name="troubleshoot-the-biztalk-esb-toolkit"></a>BizTalk ESB 工具組疑難排解

  
## <a name="installation"></a>安裝  
  
|                                       問題                                        |                                                                                                                                                                                                                                                                                                                            解決方案                                                                                                                                                                                                                                                                                                                            |
|------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    您會收到在安裝期間指派權限的 「 錯誤 」 例外狀況。     |                                                                                                                                           [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]使用標準的 BizTalk 帳戶群組，必須在安裝程序或在安裝期間將會失敗。 此外，此工具組會假設電腦所在的工作群組成員的獨立安裝或企業安裝電腦所在網域的成員。                                                                                                                                           |
| 應用程式匯入會失敗並出現錯誤訊息，會發出警告的信任層級不相符。 |                                                                                                  Microsoft.BizTalk.ESB 繫結檔案會設定為 BizTalkServerApplication 與 biztalkserverisolatedhost 主控，這接著會設定為在不受信任的模式下執行，使用預設值。 如果您已變更您的主機在信任模式下執行，將不會匯入繫結檔案。 若要修正此問題，您必須將信任層級變更為不受信任，或編輯繫結檔案，以符合您的環境中的 BizTalk 工具組 \Bindings 目錄。                                                                                                   |
| 在 網際網路資訊服務 (IIS) 未設定 Kerberos 驗證。  | 若要啟用 IIS 的 Kerberos 驗證，請參閱 Microsoft 知識庫中的下列文章：<br /><br /> -   [如何設定 IIS 以支援用於網路驗證的 Kerberos 通訊協定與 NTLM 通訊協定](http://go.microsoft.com/fwlink/?LinkId=188566)<br />-   [如何啟用 IIS 不是網域控制站的電腦上使用 Kerberos 驗證](http://go.microsoft.com/fwlink/?LinkId=188567)<br />-   [您無法設定的交涉或 NTLM 通訊協定進行 Windows 整合式驗證在 IIS 管理員中 Internet Information Services (IIS) 7.0](http://go.microsoft.com/fwlink/?LinkId=188568) |
  
## <a name="general-issues"></a>一般問題  
  
|問題|解決方案|  
|-----------|----------------|  
|將訊息傳送至泛型的 ESB 路線入口 Web 服務時，您會收到 「 內部 SOAP 處理 」 例外狀況。|若要確定 Microsoft.Practices.ESB 應用程式正在執行; 使用 BizTalk Server 管理主控台如果未執行，請加以啟動。|  
|ESB 管理入口網站中未出現例外狀況訊息。|檢查 [BizTalk 系統管理員群組概觀] 頁面和 Windows 應用程式事件記錄檔的指示將訊息傳送失敗的項目。 您可能需要重新傳送配接器 （Microsoft.Practices.ESB 應用程式的一部分） 的例外狀況設定以符合您的環境。 此外，請注意 BizTalk 失敗訊息路由的功能和 BizTalk ESB 工具組的例外狀況管理架構，產生的例外狀況訊息。 因此，請確定您啟用**失敗訊息路由**選項傳送和接收埠。|  
|當使用 WCF 服務使用靜態的解析程式，您會收到 「 無效的 SOAP 動作例外狀況。|如果 WCF 服務的 SOAP 動作不會包含目標命名空間，以下列格式中設定的解析程式中設定的 SOAP 動作值: {action} 表示不將 ESB Toolkit 的核心引擎，在執行階段串連的目標命名空間。|