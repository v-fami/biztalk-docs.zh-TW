---
title: "閱讀有關資料提供者型別在 SAP 連接字串 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Provider for SAP, connection string
- ADO, connection string
ms.assetid: 7a46eaae-604f-4bae-924b-9f6d43a6e8a0
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1a27fa8b09addc7874e6056f0b467c7f874a41e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="read-about-data-provider-types-for-the-sap-connection-string"></a>閱讀有關資料提供者型別在 SAP 連接字串
若要建立 SAP 系統的連接能力，ADO.NET 用戶端必須在連接字串的形式指定 SAP 連接屬性。 在 SAP ADO 連接字串的格式看起來像：  
  
```  
[Property1]=[Value1];[Property2]=[Value2];....  
```  
  
 連接字串來連接 SAP 系統使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]可以有下列類型：  
  
-   **類型 a:**應用程式主機型的連線所在連接 URI 會指定透過此應用程式伺服器[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]連接到 SAP 系統。  
  
-   **類型 b:**連線 URI 中指定的郵件伺服器的負載平衡的連接[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]連接到 SAP 系統。  
  
-   **類型 d:**目的地型的連線，連線 URI 中指定包含 SAP 系統的連接參數 saprfc.ini 檔案中的目的地。  
  
 下表描述這些連線指定連線 URI 中的方式。  
  
|TYPE|屬性 1|屬性 2|Description|  
|----------|----------------|----------------|-----------------|  
|只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，|ASHOST （應用程式伺服器主控件）|SYSNR （SAP 系統編號）|指定應用程式的主機型連接。|  
|B|MSHOST （郵件伺服器主機）|R3NAME （SAP R3 名稱）|指定負載平衡到郵件伺服器的連線。 對負載平衡連接，您可以指定選用的伺服器群組。|  
|D|目的地 （包含 saprfc.ini 檔案中的連接參數的目的地）|-|指定目的地型連線。 SAP 連接參數會包含在 saprfc.ini 檔案中指定的目的地。 目的地中，可以指定只有類型 A 和 B 類型的連線。 **注意：**如果 saprfc.ini 檔案中指定連接值，請確定此檔案位於相同的資料夾以存取檔案的.exe 或所需的 SAP 系統的標準位置。 如需詳細資訊，請參閱 SAP 文件集。|  
  
 根據連接字串來連接 SAP 系統使用的連接類型[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]可以包含下列屬性。  
  
|屬性|用於型別|Description|  
|--------------|-------------------|-----------------|  
|應用程式伺服器主機 (ASHOST)|只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，|SAP 應用程式伺服器主機名稱。|  
|系統編號 (SYSNR)|只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，|SAP 系統編號|  
|應用程式伺服器群組名稱 （群組）|B|SAP 伺服器群組的名稱。 這是選用的應用程式在負載平衡連接的伺服器群組。|  
|訊息伺服器主機 (MSHOST)|B|SAP 訊息伺服器主機名稱|  
|訊息伺服器服務 (MSSERV)|B|SAP 訊息伺服器服務中所指定的名稱\<系統磁碟機 >: \WINDOWS\system32\drivers\etc\services 檔案。 如果您未指定值，[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]假設這是 「 sapms\</ 3 系統名稱 >"。 例如，如果 DV1 / 3 系統名稱，此配接器會假設訊息伺服器服務名稱是"sapmsDV1"。<br /><br /> 不過，如果服務檔案中的項目不同，您必須指定該值。|  
|/ 3 系統名稱 (R3NAME)|B|SAP / 3 的名稱。|  
|目的地 （目的地）|D|從 saprfc.ini 檔案中挑選的連接參數。|  
|用戶端 （用戶端）|A、 B、 D|SAP 用戶端數目|  
|語言 (l a n g)|A、 B、 D|語言|  
|密碼 （密碼）|A、 B、 D|SAP 使用者密碼|  
|使用者名稱 （使用者）|A、 B、 D|要連接至 SAP 系統的使用者名稱|  
|啟用偵錯 (AbapDebug) 的 SAP GUI|A、 B、 D|選擇性參數，指定是否從偵錯 ABAP[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]已啟用和配接器是否使用 SAP GUI 偵錯。 這個值可以是 True 或 False。如果為 True，ABAP 偵錯已啟用，而且 SAP GUI 會開啟。 預設值是 False。|  
|追蹤 RFC SDK(RfcSdkTrace)|A、 B、 D|選擇性參數，指定是否要啟用 RFC 程式庫的追蹤。 這個值可以是 True 或 False。如果為 True，則會啟用 RFC 程式庫追蹤。 預設值是 False。|  
  
> [!NOTE]
>  屬性資料行中的括號內提供的值是必須同時提供連線 URI，透過程式設計的解決方案指定的連接屬性的名稱。 不過，如果您使用的 DDEX 外掛程式或 SQL Server 匯入和匯出精靈將 ADO 介面，連接屬性會列為好記的名稱。  
  
## <a name="example-connection-string-for-type-a"></a>類型的範例連接字串的  
 輸入的範例連接字串應該像這樣：  
  
```  
TYPE=A; ASHOST=SAPSERVER; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;  
```  
  
> [!NOTE]
>  根據預設[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]一律會考慮類型 a 的連接字串  
  
## <a name="example-connection-string-for-type-b"></a>型別 B 的範例連接字串  
 型別 B 的範例連接字串應該像這樣：  
  
```  
TYPE=B; R3NAME=NAME1; GROUP=ADAPTER; MSHOST=MSSERVER; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;  
```  
  
## <a name="example-connection-string-for-type-d"></a>類型 D 的範例連接字串  
 類型 D 的範例連接字串應該像這樣：  
  
```  
TYPE=D; DEST=TESTSAPSRV; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;  
```  
  
 範例 saprfc.ini 檔案類似：  
  
```  
DEST=TESTSAPSRV  
TYPE=A  
ASHOST=ADAPSAP47  
SYSNR=00  
```  
  
 如需 saprfc.ini 檔案的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=91457](http://go.microsoft.com/fwlink/?LinkId=91457)。  
  
 所有這三種連線類型的密碼必須包含雙引號。 不過，如果密碼會包含任何特殊字元，密碼必須括在雙引號內。 例如：  
  
```  
ASHOST=SAPSERVER; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=",@/:;_ \\";  
```  
  
> [!IMPORTANT]
>  您必須指定連接參數只能有一個連線類型 A、 B 或 d。例如，如果您在連接字串中指定的應用程式伺服器主機，您必須指定郵件伺服器主機名稱或 R3NAME。  
  
## <a name="see-also"></a>另請參閱  
 [使用.NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)