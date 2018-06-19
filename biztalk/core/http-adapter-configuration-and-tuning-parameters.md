---
title: HTTP 配接器組態和調整參數 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HTTP adapters, parameters
- configuring [HTTP adapters], parameters
- HTTP adapters, tuning
- RequestQueueSize key [HTTP adapters]
- HttpReceiveThreadsPerCpu key [HTTP adapters]
- HttpOutTimeoutInterval key [HTTP adapters]
- HttpOutInflightSize key [HTTP adapters]
- configuring [HTTP adapters], tuning
- DisableChunkEncoding key [HTTP adapters]
- HttpOutCompleteSize key [HTTP adapters]
ms.assetid: c8989a88-722a-40b5-94cf-4b6840add02e
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5db4f4dc4403ddfbf677ac2729c00e2b1976db61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257782"
---
# <a name="http-adapter-configuration-and-tuning-parameters"></a>HTTP 配接器組態和調整參數
HTTP 配接器可以透過登錄機碼項目和修改位於 BizTalk Server 安裝根目錄的 BTSNTSvc.exe.config 檔案，來存取組態和調整參數。  
  
 **影響 HTTP 配接器效能的登錄設定**  
  
 下表描述會影響 HTTP 配接器效能的登錄設定。 請注意，依照預設，在登錄中沒有 HTTP 配接器機碼，所以 HTTP 配接器會使用預設值。 若有必要變更預設值，您必須在登錄的下列位置建立以下登錄機碼：  
  
-   **DisableChunkEncoding**， **RequestQueueSize**，和**HttpReceiveThreadsPerCpu**必須定義在**碼BTSSvc.3.0\HttpReceive**。  
  
-   **HttpOutTimeoutInterval**， **HttpOutInflightSize**，和**HttpOutCompleteSize**必須定義在**碼BTSSvc {GUID}** 其中**GUID**是 HTTP 傳送處理常式主控件的識別碼。  
  
|機碼名稱|類型|預設值|說明|  
|--------------|----------|-------------|-----------------|  
|**DisableChunkEncoding**|DWORD|0|控制 HTTP 接收配接器在傳送回應給用戶端時是否使用區塊編碼。<br /><br /> 設成非零值以關閉 HTTP 接收配接器回應的區塊編碼。<br /><br /> **最小值：** 0<br /><br /> **最大值：** 任何非零值|  
|**Requestqueuesize 機**|DWORD|256|定義 HTTP 接收配接器一次處理的並行要求數目。<br /><br /> **最小值：** 10<br /><br /> **最大值：** 2048年|  
|**Httpreceivethreadspercpu 機**|DWORD|2|定義配置給 HTTP 接收配接器的每個 CPU 的執行緒數目。<br /><br /> **最小值：** 1<br /><br /> **最大值：** 10|  
|**HttpOutTimeoutInterval**|DWORD|2000|定義 HTTP 傳送配接器在逾時前等候的間隔 (以秒為單位)。<br /><br /> **最小值：** 500<br /><br /> **最大值：** 10000000|  
|**HttpOutInflightSize**|DWORD|100|這是 BizTalk Server HTTP 傳送配接器執行個體將處理的並行 HTTP 要求數目上限。<br /><br /> 建議的延遲值是介於 3 到 5 倍， **maxconnection**組態檔項目，如下所示。<br /><br /> **最小值：** 1<br /><br /> **最大值：** 1024年|  
|**HttpOutCompleteSize**|DWORD|5|控制 HTTP 傳送配接器傳回的訊息批次大小。 如果緩衝區未滿，而且有待處理的回應配接器將會等候 1 秒，直到它會認可批次。  低延遲案例這應該設定為 1，以允許配接器立即傳送回應訊息到 messagebox 進行處理。<br /><br /> **最小值：** 1<br /><br /> **最大值：** 1024年|  
  
 **組態檔項目來管理 HTTP 傳送配接器對特定目的地伺服器的同時連線數**  
  
 您可透過在根 BizTalk Server 安裝目錄的 BTSNTSvc.exe 組態檔建立一個項目，以設定 HTTP 配接器為特定目的地伺服器開啟的並行連線數目。  
  
> [!NOTE]
>  若 HTTP 和 SOAP 配接器傳送訊息至相同的目的地 HTTP 伺服器，此屬性就會套用至 HTTP 和 SOAP 配接器。 “maxconnnection”屬性的預設值為 2，可為所有 URI 的“maxconnection”屬性設定的最大值為 20。  
  
 下列是連線上限屬性的組態範例。  
  
```  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "20" />  
      <add address = "http://www.northwind.com" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [設定 HTTP 配接器](../core/configuring-the-http-adapter.md)