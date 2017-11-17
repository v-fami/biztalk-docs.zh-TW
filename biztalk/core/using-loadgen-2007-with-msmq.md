---
title: "搭配 MSMQ 使用 LoadGen 2007 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8f23a86-0e6d-478a-87a3-5b02338c9afb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55d67628b7863df3f2396cd9b45b55f42a488b8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-loadgen-2007-with-msmq"></a><span data-ttu-id="7fa90-102">搭配 MSMQ 使用 LoadGen 2007</span><span class="sxs-lookup"><span data-stu-id="7fa90-102">Using LoadGen 2007 with MSMQ</span></span>
<span data-ttu-id="7fa90-103">「負載產生」工具 Loadgen 可讓您在 BizTalk Server 系統上模擬負載過重的情形。</span><span class="sxs-lookup"><span data-stu-id="7fa90-103">The Load Generation tool, Loadgen, enables you to simulate heavy loads on a BizTalk Server system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7fa90-104">LoadGen 2007 工具是下載[http://go.microsoft.com/fwlink/?LinkId=59841](http://go.microsoft.com/fwlink/?LinkId=59841)。</span><span class="sxs-lookup"><span data-stu-id="7fa90-104">The LoadGen 2007 tool is available for download at [http://go.microsoft.com/fwlink/?LinkId=59841](http://go.microsoft.com/fwlink/?LinkId=59841).</span></span>  
  
 <span data-ttu-id="7fa90-105">我們雖然支援搭配 MSMQ 使用 LoadGen，但是我們不會在安裝期間自動註冊 MSMQ COM 元件，因為您的電腦上可能沒有安裝 MSMQ 執行階段服務。</span><span class="sxs-lookup"><span data-stu-id="7fa90-105">Using LoadGen with MSMQ is supported, but we do not auto-register the MSMQ COM components during installation since the MSMQ runtime service may not be installed on your computer.</span></span>  
  
 <span data-ttu-id="7fa90-106">若要使用 MSMQ 和 LoadGen，請以手動註冊位於 bins 目錄中的 MSMQTransmitter.dll 和 ComMsmqMonitor.dll 檔案：</span><span class="sxs-lookup"><span data-stu-id="7fa90-106">To use MSMQ and LoadGen, manually register the MSMQTransmitter.dll and ComMsmqMonitor.dll files located in the bins directory:</span></span>  
  
```  
regsvr32 MSMQTransmitter.dll  
```  
  
 <span data-ttu-id="7fa90-107">如果您沒有註冊 MSMQ COM 元件，便會收到下列執行階段錯誤：</span><span class="sxs-lookup"><span data-stu-id="7fa90-107">If you do not register the MSMQ COM components, you will receive the following runtime errors:</span></span>  
  
```  
Cannot Load Transport DLL C:\Program Files\LoadGen\Bins\MSMQTransport.dll for Section MSMQRxQTxn   
Exception has been thrown by the target of an invocation.  
```  
  
## <a name="see-also"></a><span data-ttu-id="7fa90-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fa90-108">See Also</span></span>  
 [<span data-ttu-id="7fa90-109">測量引擎 MST 的測試案例</span><span class="sxs-lookup"><span data-stu-id="7fa90-109">Test Scenarios for Measuring MST of the Engine</span></span>](../core/test-scenarios-for-measuring-mst-of-the-engine.md)