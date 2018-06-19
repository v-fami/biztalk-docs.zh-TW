---
title: 停用 Windows Server 2003 SP1 與 SP2 阻斷服務檢查 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8822c1e4-d146-4361-b25a-7b81cd5cdd3b
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b33333efd055a659557513ecc8e0b53a42bc30ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22297710"
---
# <a name="disabling-windows-server-2003-sp1-and-sp2-denial-of-service-checking"></a>停用 Windows Server 2003 SP1 與 SP2 阻斷服務檢查
> [!NOTE]  
>  本主題是只適用於 Windows Server 2003。  
  
 您應該停用 Windows Server 2003 Service Pack 1 和 Service Pack 2 的阻絕服務檢查。 這是因為某些高負載情況下，在 Windows Server 2003 SP1 和 SP2 的阻絕服務檢查可能不正確地識別有效的 TCP/IP 連線為阻絕服務攻擊。  
  
> [!IMPORTANT]  
>  您應該停用這項功能只能在內部網路案例中的，當您確定您將不會發生實際阻絕服務攻擊。  
  
## <a name="how-denial-of-service-can-affect-tcpip-connections"></a>阻絕服務會如何影響 TCP/IP 連接  
 Windows Server 2003 SP1 和 SP2 實作的安全性功能會減少佇列的並行 TCP/IP 連線到伺服器的大小。 此功能可防止阻絕服務的攻擊。 在大量負載的情況下在 Windows Server 2003 SP1 或更新版本的 TCP/IP 通訊協定可能不正確地識別有效的 TCP/IP 連線為阻絕服務攻擊。 這可能是因為當[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]負載過重。  
  
## <a name="modifying-the-registry-entry"></a>修改的登錄項目  
 如需詳細資訊，請參閱 Microsoft 知識庫文章 899599， [「 BizTalk Server 主控件執行個體失敗，和 BizTalk Server 為基礎的伺服器處理大量文件時，' 一般網路 」 錯誤會寫入應用程式記錄檔 」](http://go.microsoft.com/fwlink/?LinkId=158860) (http://go.microsoft.com/fwlink/?LinkId=158860)。 請遵循本文章中的指示，建立**SynAttackProtect**該主控件執行 SQL Server 的電腦上的登錄項目[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫和執行的任何電腦上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行 Windows Server2003 SP1 或更新版本。  
  
## <a name="tuning-registry-settings-that-govern-the-level-of-denial-of-service-attack-protection"></a>調整控管的阻絕服務攻擊的保護層級的登錄設定  
 在某些情況下您可能想要維護阻斷服務保護但降低阻絕服務功能套用的積極程度。 您可微調的阻絕服務保護功能的預設行為，依照下列步驟：  
  
1.  請確認**SynAttackProtect**的 REG_DWORD 值設定登錄項目**1**述[http://go.microsoft.com/fwlink/?LinkId=111477](http://go.microsoft.com/fwlink/?LinkId=111477)。  
  
2.  設定**TcpMaxHalfOpen**登錄項目述[http://go.microsoft.com/fwlink/?LinkId=111478](http://go.microsoft.com/fwlink/?LinkId=111478)。  
  
3.  設定**TcpMaxHalfOpenRetried**登錄項目述[http://go.microsoft.com/fwlink/?LinkId=111479](http://go.microsoft.com/fwlink/?LinkId=111479)。  
  
## <a name="see-also"></a>另請參閱  
 [操作的整備檢查清單](../technical-guides/operational-readiness-checklists.md)