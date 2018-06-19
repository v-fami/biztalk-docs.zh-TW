---
title: 解析程式的 Web 服務 |Microsoft 文件
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
ms.openlocfilehash: 916181431686ca729c0751d9362570afb7dddeee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295214"
---
# <a name="the-resolver-web-service"></a>解析程式的 Web 服務
解析程式 Web 服務是一個閘道到 ESB 動態解析機制。 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含此服務的兩個版本： ASP.NET (ASMX) 版本和 Windows Communication Foundation (WCF) 版本。 服務名稱就是**ESB。ResolverServices**和**ESB。ResolverServices.WCF**分別和服務會公開下列方法：  
  
-   **解決。** 這個方法會採用做為其單一參數**字串**，其中包含解析程式的連接字串，針對要求符合標準的連接字串的已註冊的解析程式例如**靜態、 BRE、 UDDI，XPATH、 路線、 路線靜態、 BRI，** 或**LDAP。**  
  
-   **ResolveMessage。** 這個方法會採用做為其第一個參數包含要求中，符合標準的連接字串的已註冊的解析程式這類的解析程式連接字串的字串**靜態、 BRE、 UDDI、 XPATH、 路線，行程靜態、 BRI，** 或**LDAP**。 此外，該方法會接受選擇性的第二個參數，做為**字串**包含服務可以使用做為選擇性的事實，以協助解決的 XML 訊息文件; 例如，BRE 解析程式可能需要訊息本文封裝事實。  
  
 如需解析器和 ResolverDictionary 類別和其使用方式的詳細資訊，請參閱[使用協助程式類別](../esb-toolkit/using-the-helper-classes.md)。  
  
## <a name="resolver-connection-strings"></a>解析程式的連接字串  
 ESB 動態解析機制會使用連接字串，加上表示的解析度來執行類型的 moniker。 包含支援的 moniker**靜態、 BRE、 UDDI、 UDDI3、 XPATH、 路線、 路線靜態、 BRI，** 和**LDAP**。 下列連接字串示範**UDDI** moniker:  
  
```  
  
//UDDI  
UDDI:\\serverUrl=http://localhost/uddi;serviceName=PurchaseOrder;serviceProvider=Microsoft.Practices.ESB  
```  
  
 如需支援的動態解析機制的連接字串的類型資訊，請參閱[使用動態解析和路由](../esb-toolkit/using-dynamic-resolution-and-routing.md)。  
  
> [!NOTE]
>  您必須設定此服務使用 Windows 整合式安全性，以及內建網路服務帳戶下執行。  
>   
>  根據預設，解析程式的 Web 服務不會設定為需要安全通訊端層 (SSL) 用戶端存取時。 您應該設定服務，讓需要 SSL 用戶端存取，並保護網際網路資訊服務 (IIS) Web 服務主機電腦與您使用網路層級 IPSec 和適當的檔案層級存取權的 BizTalk Server 之間的連線控制清單 (ACL) 權限。 若要避免安全性風險，不建議以公開此服務的受信任的子系統界限之外。