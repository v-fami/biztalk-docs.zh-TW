---
title: 解析程式 Web 服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 236cff15-562a-41d5-bfdc-d250186fb616
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3cd153a8ceeba983c71854d02854e37ed046e1bd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987527"
---
# <a name="the-resolver-web-service"></a>解析程式 Web 服務
解析程式 Web 服務是到 ESB 動態解析機制。 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] 包含此服務的兩個版本： ASP.NET (ASMX) 版本和 Windows Communication Foundation (WCF) 版本。 服務名稱為**ESB。ResolverServices**和**ESB。ResolverServices.WCF**，分別與服務會公開下列方法：  
  
- **解決。** 這個方法會採用做為其單一參數**字串**，其中包含符合標準的連接字串的已註冊的解析程式這類要求的解析程式連接字串**靜態、 BRE、 UDDI、XPATH，路線，路線靜態、 BRI，** 或**LDAP。**  
  
- **ResolveMessage。** 這個方法會採用做為其第一個參數包含要求中，符合標準的連接字串的已註冊的解析程式這類的解析程式連接字串的字串**靜態、 BRE、 UDDI、 XPATH、 路線，路線-BRI，靜態**或是**LDAP**。 此外，該方法會接受選擇性的第二個參數，做為**字串**，其中包含 XML 訊息文件服務以協助解決時，可用做為選擇性的事實; 比方說，BRE 解析程式可能會要求訊息內文封裝的事實。  
  
  如需有關的解析程式和 ResolverDictionary 類別和其使用方式的詳細資訊，請參閱[使用協助程式類別](../esb-toolkit/using-the-helper-classes.md)。  
  
## <a name="resolver-connection-strings"></a>解析程式的連接字串  
 ESB 動態解析機制會使用連接字串，加上表示的解析度，以執行類型的 moniker。 包含支援的 moniker**靜態、 BRE、 UDDI、 UDDI3、 XPATH、 路線，路線靜態、 BRI，** 並**LDAP**。 下列連接字串顯示的範例**UDDI** moniker:  
  
```  
  
//UDDI  
UDDI:\\serverUrl=http://localhost/uddi;serviceName=PurchaseOrder;serviceProvider=Microsoft.Practices.ESB  
```  
  
 如需使用動態解析機制所支援的連接字串的類型資訊，請參閱[使用動態解析和路由](../esb-toolkit/using-dynamic-resolution-and-routing.md)。  
  
> [!NOTE]
>  您必須設定此服務使用 Windows 整合式安全性，以及內建的網路服務帳戶下執行。  
>   
>  根據預設，解析程式 Web 服務未設定為需要 Secure Sockets Layer (SSL) 用戶端存取時。 您應該設定服務，因此它需要 SSL 用戶端存取和保護 Internet Information Services (IIS) Web 服務主機電腦與您使用網路層級 IPSec 和適當的檔案層級存取權的 BizTalk Server 之間的連線控制清單 (ACL) 權限。 若要避免安全性風險，不建議您使用這項服務的受信任的子系統界限之外公開 （expose）。