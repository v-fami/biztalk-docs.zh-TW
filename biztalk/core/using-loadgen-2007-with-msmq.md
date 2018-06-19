---
title: 搭配 MSMQ 使用 LoadGen 2007 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8f23a86-0e6d-478a-87a3-5b02338c9afb
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55d67628b7863df3f2396cd9b45b55f42a488b8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287126"
---
# <a name="using-loadgen-2007-with-msmq"></a>搭配 MSMQ 使用 LoadGen 2007
「負載產生」工具 Loadgen 可讓您在 BizTalk Server 系統上模擬負載過重的情形。  
  
> [!NOTE]
>  LoadGen 2007 工具是下載[http://go.microsoft.com/fwlink/?LinkId=59841](http://go.microsoft.com/fwlink/?LinkId=59841)。  
  
 我們雖然支援搭配 MSMQ 使用 LoadGen，但是我們不會在安裝期間自動註冊 MSMQ COM 元件，因為您的電腦上可能沒有安裝 MSMQ 執行階段服務。  
  
 若要使用 MSMQ 和 LoadGen，請以手動註冊位於 bins 目錄中的 MSMQTransmitter.dll 和 ComMsmqMonitor.dll 檔案：  
  
```  
regsvr32 MSMQTransmitter.dll  
```  
  
 如果您沒有註冊 MSMQ COM 元件，便會收到下列執行階段錯誤：  
  
```  
Cannot Load Transport DLL C:\Program Files\LoadGen\Bins\MSMQTransport.dll for Section MSMQRxQTxn   
Exception has been thrown by the target of an invocation.  
```  
  
## <a name="see-also"></a>另請參閱  
 [測量引擎 MST 的測試案例](../core/test-scenarios-for-measuring-mst-of-the-engine.md)