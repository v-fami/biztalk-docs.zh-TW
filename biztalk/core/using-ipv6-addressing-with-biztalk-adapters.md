---
title: 使用 IPv6 定址與 BizTalk 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93cd2ead-5e87-47ac-8f78-d56b80afd34e
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73047c13c5ea328dd71807a3ba7eea79ddee87ce
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003687"
---
# <a name="using-ipv6-addressing-with-biztalk-adapters"></a>BizTalk 配接器搭配使用 IPv6 定址
BizTalk Server 配接器支援使用 IPv6 定址。 本主題說明指定 UNC 路徑的 IPv6 位址時應該使用的術語表、指定常值 IPv6 位址時必須使用的術語表，以及與 HTTP 和 SOAP 配接器搭配使用 IPv6 範圍識別項。  
  
## <a name="ipv6-address-nomenclature-used-for-a-unc-path"></a>UNC 路徑所用的 IPv6 位址術語表  
 指定 UNC 路徑中的常值 IPv6 位址時，請遵循這些步驟：  
  
1. 取代任何冒號":"取代任何冒號"-"字元。  
  
2. 將文字附加"**ipv6-literal.net**」 的 IP 位址。  
  
   例如，URI 若指向 IPv6 位址為 2001:DB8:2a:1005:230:48ff:fe73:989d 之電腦的檔案共用，其術語表為：  
  
```  
\\2001-DB8-2a-1005-230-48ff-fe73-989d.ipv6-literal.net\<sharename\>  
```  
  
 何處\< *sharename* \>是目標電腦上的檔案共用的名稱。  
  
> [!NOTE]
>  執行 File 傳送和接收處理常式之主控件執行個體的使用者帳戶，一定要有檔案共用的適當權限。 如需 File 配接器接收檔案的資料夾權限的詳細資訊請參閱 <<c0> [ 設定檔案接收處理常式](../core/configure-the-file-adapter.md)。 如需傳送 File 配接器的檔案時的資料夾權限的詳細資訊請參閱[File 配接器的已知問題](../core/known-issues-with-the-file-adapter.md)。 如需支援使用 File 配接器的檔案系統資訊，請參閱[ http://support.microsoft.com/kb/815070 ](http://support.microsoft.com/kb/815070)。  
  
## <a name="using-ipv6-scope-identifiers-with-the-http-adapter-and-the-soap-send-adapter"></a>與 HTTP 配接器和 SOAP 傳送配接器搭配使用 IPv6 範圍識別項  
 HTTP 傳送和接收配接器和 SOAP 傳送配接器需要的如果使用 IPv6 位址的範圍識別項時，範圍識別項必須以逸出的逸出程式碼 **%25**。 例如， **fe80::550c:489f:e65e:aef3%8**是有效的 IPv6 位址，其中包含的範圍識別項 (%8)。 若要將此 IPv6 位址搭配使用 HTTP 傳送和接收配接器或 SOAP 傳送配接器，範圍識別項必須跳過，如下所示：  
  
```  
fe80::550c:489f:e65e:aef3%258  
```  
  
## <a name="adapter-uri-nomenclature-used-for-a-literal-ipv6-address"></a>常值 IPv6 位址所用的配接器 URI 術語表  
  
-   配接器 URI 若要使用常值 IPv6 位址，必須使用方括號 "[" 和 "]" 括住 IP 位址。 例如，URI 含 IPv6 位址 2001:DB8:2a:1005:230:48ff:fe73:989d 的術語表為：  
  
    ```  
    [2001:DB8:2a:1005:230:48ff:fe73:989d]  
    ```  
  
    > [!NOTE]
    >  使用常值 IPv6 位址的配接器 Uri 中所建立的指導方針[RFC2732](http://go.microsoft.com/fwlink/?LinkId=90375)。  
  
-   指定常值 IPv6 位址做為 POP3 接收配接器、SMTP 傳送配接器，或 SQL 傳送和接收配接器的伺服器名稱時，不應使用方括號括住 IPv6 位址。  
  
## <a name="summary-of-considerations-when-using-literal-ipv6-addressing-with-biztalk-adapters"></a>常值 IPv6 定址與 BizTalk 配接器搭配使用時之考量的摘要  
 下表摘要說明，使用常值 IPv6 位址何時需要以方括號 "[" 和 "]" 括住 IP 位址，以及何時必須跳過用於 IPv6 位址中的範圍識別項：  
  
|配接器|常值 IPv6 位址必須以方括號括住嗎？|範圍識別項必須跳過嗎？|  
|---|---|---|  
|POP3 接收|否|否|  
|SMTP 傳送|否|否|  
|SQL 傳送和接收|否|否|  
|File 傳送和接收|否 (請參見**IPv6 位址術語表用於 UNC 路徑**)|否|  
|HTTP 傳送和接收|是|是|  
|MQSeries 傳送和接收|是|否|  
|MSMQ 傳送和接收|是|否|  
|SOAP 傳送|是|是|  
|SOAP 接收|是|否|  
|WCF 傳送和接收|是|否|