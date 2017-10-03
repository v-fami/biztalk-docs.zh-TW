---
title: "重新提交的問題進行疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b60ad45-d793-4de6-b9bc-3e8ef34f2b61
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1a143924b97117a708caea3006f74db6e029ca4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-resubmission-issues"></a><span data-ttu-id="3c564-102">重新提交的問題進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="3c564-102">Troubleshooting Resubmission Issues</span></span>
<span data-ttu-id="3c564-103">如果您有重新提交訊息的問題，請檢查下列各項：</span><span class="sxs-lookup"><span data-stu-id="3c564-103">If you have problems resubmitting messages, check the following:</span></span>  
  
-   <span data-ttu-id="3c564-104">您可以透過瀏覽器存取接收位置嗎？</span><span class="sxs-lookup"><span data-stu-id="3c564-104">Can you access the receive location through your browser?</span></span> <span data-ttu-id="3c564-105">如果您嘗試重新提交到 WCF 上手或 SOAP 上手，URL 應該表單 http://localhost/ESB.OnRampServices.WCF/ProcessItinerary.svc 或 http://localhost/ESB.OnRampServices/ProcessItinerary.asmx。</span><span class="sxs-lookup"><span data-stu-id="3c564-105">If you are trying to resubmit to the WCF on-ramp or the SOAP on-ramp, the URL should be of the form http://localhost/ESB.OnRampServices.WCF/ProcessItinerary.svc or http://localhost/ESB.OnRampServices/ProcessItinerary.asmx.</span></span> <span data-ttu-id="3c564-106">如果您嘗試重新提交到 HTTP 接收位置，您可以使用網際網路瀏覽器，判斷是否接收位置是否運作正確將範例訊息附加到查詢字串，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="3c564-106">If you are trying to resubmit to an HTTP receive location, you can use your Internet browser to determine whether the receive location is functioning properly by appending a sample message to the query string, as shown in the following example.</span></span>  
  
    ```  
    http://localhost/HTTPOnRamp/BTSHttpReceive.dll?<SampleMessage>Sample Message Content</SampleMessage>  
    ```  
  
-   <span data-ttu-id="3c564-107">確認 BizTalk HTTP 接收配接器已正確設定。</span><span class="sxs-lookup"><span data-stu-id="3c564-107">Verify that the BizTalk HTTP receive adapter is properly configured.</span></span>