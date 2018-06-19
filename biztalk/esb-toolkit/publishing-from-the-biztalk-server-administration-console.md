---
title: 從 BizTalk Server 管理主控台中發行 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b78b1981-b227-4cf5-9435-6fc57963552a
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbe03b1a8df67581ce73db31cd5ed4b80b7a109c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26009095"
---
# <a name="publishing-from-the-biztalk-server-administration-console"></a>從 BizTalk Server 管理主控台中發行
如果您想要管理透過 BizTalk Server 管理主控台，而不是在 ESB 管理入口網站發行端點，您可以在結束點的描述欄位中輸入通用描述、 探索與整合 (UDDI) moniker若要發行至 UDDI。 以下是範例 moniker。  
  
```  
uddi://TransportType=other;Status=Published.  
```  
  
 您可以設定下列的 UDDI 屬性使用**描述**欄位在 BizTalk Server 管理主控台：  
  
-   **ModifiedBy**。 此選擇性屬性包含修改端點; 的使用者帳戶名稱例如，MyDomainName\MyUserName。  
  
-   **UDDIContact**。 此選用性屬性是使用者的定義為 UDDI 的商業提供者的連絡人名稱。  
  
-   **UDDIUserType**。 此選用性屬性是使用者的定義為 UDDI 的商業提供者的使用者類型。  
  
-   **UDDIEmail**。 此選用性屬性是使用者的定義為 UDDI 的商業提供者電子郵件地址。  
  
-   **TransportType**。 此選用性屬性是端點配接器類型，例如**檔案、 MQS、 Wcf-wshttp、 SOAP、 HTTP、** 或**FTP**。  
  
-   **狀態**。 此選用性屬性是狀態的端點，例如**發佈**或**暫止**。 UDDI 發行服務會使用此屬性以探索端點的狀態。  
  
-   **BindingType**。 此選擇性屬性為特定的通訊協定 （URL 類型） 的 UDDI 繫結支援，例如**mailto、 http、 https、 ftp、 傳真、 phone**或**其他**。 UDDI 發行服務會使用這個屬性，來建立端點的繫結。