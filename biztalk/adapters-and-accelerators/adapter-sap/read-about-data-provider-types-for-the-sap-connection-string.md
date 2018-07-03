---
title: 了解資料提供者類型的 SAP 連接字串 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Data Provider for SAP, connection string
- ADO, connection string
ms.assetid: 7a46eaae-604f-4bae-924b-9f6d43a6e8a0
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 142afd61966640e004e3dc1160c5ce486984d8e6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013423"
---
# <a name="read-about-data-provider-types-for-the-sap-connection-string"></a>了解資料提供者類型的 SAP 連接字串
若要建立 SAP 系統的連線，ADO.NET 用戶端必須在連接字串的形式指定 SAP 連接屬性。 SAP ADO 連接字串的格式看起來像：  

```  
[Property1]=[Value1];[Property2]=[Value2];....  
```  

 若要連接到 SAP 系統使用的連接字串[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]可以有下列類型：  

- **類型 a:** 應用程式主機型的連線所在的連線 URI 指定的應用程式伺服器透過此[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]連線到 SAP 系統。  

- **類型 b**所在的連線 URI 會指定透過它的訊息伺服器的負載平衡的連線[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]連線到 SAP 系統。  

- **類型 d:** 目的地型的連線，連線 URI 中指定包含 SAP 系統的連線參數 saprfc.ini 檔案中的目的地。  

  下表描述這些連線的連線 URI 中指定的方式。  

|TYPE|屬性 1|屬性 2|描述|  
|----------|----------------|----------------|-----------------|  
|只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，|ASHOST （應用程式伺服器主控件）|SYSNR （SAP 系統編號）|指定應用程式的主機型連接。|  
|B|MSHOST （郵件伺服器主機）|R3NAME （SAP R3 名稱）|指定負載平衡透過郵件伺服器的連線。 負載平衡連線，可指定選擇性的伺服器群組。|  
|D|目的地 （包含 saprfc.ini 檔案中的連線參數的目的）|-|指定的目的地型連線。 SAP 連接參數會包含在 saprfc.ini 檔案中指定的目的地。 目的地中，可以指定只有型別 A 和 B 類型的連線。 **注意：** saprfc.ini 檔案中指定連接值，請確定該檔案位於相同的資料夾存取檔案的.exe 或所需的 SAP 系統的標準位置中。 如需詳細資訊，請參閱 SAP 文件。|  

 根據連線，連接到 SAP 系統使用的連接字串的型別[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]可以包含下列屬性。  


|               屬性                | 用於型別 |                                                                                                                                                                                                                                               描述                                                                                                                                                                                                                                                |
|---------------------------------------|---------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   應用程式伺服器主機 (ASHOST)    |       只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，       |                                                                                                                                                                                                                                 SAP 應用程式伺服器主機名稱。                                                                                                                                                                                                                                 |
|         系統編號 (SYSNR)         |       只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，       |                                                                                                                                                                                                                                          SAP 系統編號                                                                                                                                                                                                                                           |
| 應用程式伺服器群組名稱 （群組） |       B       |                                                                                                                                                                                              SAP 伺服器群組的名稱。 這是選用的負載平衡連線中的應用程式伺服器群組。                                                                                                                                                                                              |
|     訊息伺服器主機 (MSHOST)      |       B       |                                                                                                                                                                                                                                   SAP 訊息伺服器主機名稱                                                                                                                                                                                                                                    |
|    訊息伺服器服務 (MSSERV)    |       B       | SAP 訊息伺服器服務中所指定的名稱\<系統磁碟機\>: \WINDOWS\system32\drivers\etc\services 檔案。 如果您未指定值，[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]假設這是 「 sapms\<R/3 系統名稱\>"。 例如，如果 DV1 R/3 系統名稱，此配接器會假設訊息伺服器服務名稱是"sapmsDV1 」。<br /><br /> 不過，如果服務檔中的項目不同，您必須指定該值。 |
|       R/3 系統名稱 (R3NAME)        |       B       |                                                                                                                                                                                                                                            SAP R/3 名稱。                                                                                                                                                                                                                                             |
|          目的地 (DEST)           |       D       |                                                                                                                                                                                                                        從 saprfc.ini 檔案中挑選的連線參數。                                                                                                                                                                                                                         |
|            用戶端 （用戶端）            |     A、 B、 D     |                                                                                                                                                                                                                                          SAP 用戶端數目                                                                                                                                                                                                                                           |
|            語言 （語言）            |     A、 B、 D     |                                                                                                                                                                                                                                                 語言                                                                                                                                                                                                                                                 |
|           密碼 （密碼）           |     A、 B、 D     |                                                                                                                                                                                                                                          SAP 使用者密碼                                                                                                                                                                                                                                           |
|            使用者名稱 （使用者）            |     A、 B、 D     |                                                                                                                                                                                                                                要連接到 SAP 系統的使用者名稱                                                                                                                                                                                                                                 |
| 啟用偵錯 (AbapDebug) 的 SAP GUI  |     A、 B、 D     |                                                                                      選擇性參數，指定是否從偵錯 ABAP[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]啟用和配接器是否使用 SAP GUI 偵錯。 此值可以是 True 或 False。如果為 True，啟用 ABAP 偵錯，而且 SAP GUI 會開啟。 預設值是 False。                                                                                      |
|      追蹤 RFC SDK(RfcSdkTrace)       |     A、 B、 D     |                                                                                                                                                                 指定是否要啟用 RFC 程式庫追蹤的選擇性參數。 此值可以是 True 或 False。如果為 True，則會啟用 RFC 程式庫的追蹤。 預設值是 False。                                                                                                                                                                 |

> [!NOTE]
>  屬性資料行中的括號內提供的值所提供的連線 URI，透過程式設計的解決方案時，必須指定連接屬性的名稱。 不過，如果您使用的 DDEX 外掛程式或 SQL Server 匯入和匯出精靈使用 ADO 介面，連接屬性將會列為易記名稱。  

## <a name="example-connection-string-for-type-a"></a>類型的範例連接字串的  
 輸入的連接字串範例如下：  

```  
TYPE=A; ASHOST=SAPSERVER; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;  
```  

> [!NOTE]
>  根據預設[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]一律會考慮連接字串的型別 a。  

## <a name="example-connection-string-for-type-b"></a>型別 B 的範例連接字串  
 類型 b 連接字串範例如下：  

```  
TYPE=B; R3NAME=NAME1; GROUP=ADAPTER; MSHOST=MSSERVER; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;  
```  

## <a name="example-connection-string-for-type-d"></a>輸入 D 的範例連接字串  
 輸入 D 的連接字串範例如下：  

```  
TYPE=D; DEST=TESTSAPSRV; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=YourPassword;  
```  

 Saprfc.ini 檔案範例如下：  

```  
DEST=TESTSAPSRV  
TYPE=A  
ASHOST=ADAPSAP47  
SYSNR=00  
```  

 如需有關 saprfc.ini 檔案的詳細資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkId=91457 ](http://go.microsoft.com/fwlink/?LinkId=91457)。  

 所有這三種連線類型的密碼必須包含雙引號。 不過，如果密碼包含任何其他特殊字元，密碼就必須括在雙引號內。 例如：  

```  
ASHOST=SAPSERVER; SYSNR=00; CLIENT=800; LANG=EN; USER=YourUserName; PASSWD=",@/:;_ \\";  
```  

> [!IMPORTANT]
>  您必須指定連接參數只能有一個連線類型 A、 B 或 d。例如，如果您在連接字串中指定的應用程式伺服器主機，您必須指定郵件伺服器主機名稱或 R3NAME。  

## <a name="see-also"></a>另請參閱  
 [使用 .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)