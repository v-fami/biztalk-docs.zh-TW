---
title: "設計安全架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- firewalls
- architecture, security
- installation, firewalls
- installation, security
ms.assetid: 93df6a3f-396c-4767-99c8-2145bddf8fdf
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 157c11477efb9dec455e9ac2de81736cd4ea72ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="designing-a-secure-architecture"></a>設計安全架構
完成 BizTalk Server 部署的系統架構的詳細資訊，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。  
  
 主題中所提供的架構[大型分散式架構](../core/large-distributed-architecture.md)解決了許多 BizTalk 環境是易受攻擊的潛在安全性威脅。 不過，您需要評估您的商務判斷提示、您的商務所關心的威脅以及可以保護您的判斷提示並減輕潛在威脅的資源，以確定最適於您的架構。 本節提供設計 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 架構時您可以考量的其他安全性選項。  
  
## <a name="firewalls"></a>防火牆  
 您可以使用實體 (硬體) 或軟體防火牆來限制存取環境中的資源。 雖然本主題[大型分散式架構](../core/large-distributed-architecture.md)使用 Forefront Threat Management Gateway (TMG) 2010 server，您可以使用硬體或協力廠商軟體防火牆、 建立類似的架構，只要您開啟和設定不同的 BizTalk Server 元件之間的通訊時所需的連接埠。 如需 BizTalk Server 使用的連接埠的詳細資訊，請參閱[所需的 BizTalk Server 的連接埠](../core/required-ports-for-biztalk-server.md)。  
  
## <a name="active-directory"></a>Active Directory  
 在範例部署中，可以使用 Active Directory® 目錄服務，在每個伺服器群組周圍建立堅固的安全界限。 您可以使用單向信任，進一步保護 BizTalk Server 環境免於遭到在處理伺服器上執行的其他非 BizTalk Server 應用程式缺陷的攻擊，而使用在資料網域中建立的帳戶來執行 BizTalk Server 應用程式。 因為資料網域不信任其他網域中的任何帳戶，所以其他網域中帳戶的洩漏仍可保持 BizTalk Server 環境免於受害。  
  
## <a name="ipsec-and-ssl"></a>IPSec 與 SSL  
 若您的環境沒有造成需要提供安全性防火牆層級的重要威脅，但是連接資料、處理以及服務網域的網路區段並未實際防護各種網路攻擊 (例如封包探查或竄改)，則您仍需要保護在伺服器之間傳送的資料。 在此狀況下，建議您使用「網際網路通訊協定安全性」(IPSec) 或「安全通訊端層」(SSL) 來加密伺服器之間的流量。  
  
## <a name="see-also"></a>另請參閱  
 [設計分散式的架構](../core/designing-a-distributed-architecture.md)   
 [安全性規劃](../core/planning-for-security.md)   
 [設計 BizTalk Server 的系統架構](../core/designing-the-system-architectures-for-biztalk-server.md)   
 [BizTalk Server 架構範例](../core/sample-biztalk-server-architectures.md)