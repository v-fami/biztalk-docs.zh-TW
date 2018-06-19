---
title: 重新提交的問題進行疑難排解 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b60ad45-d793-4de6-b9bc-3e8ef34f2b61
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1a143924b97117a708caea3006f74db6e029ca4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295094"
---
# <a name="troubleshooting-resubmission-issues"></a>重新提交的問題進行疑難排解
如果您有重新提交訊息的問題，請檢查下列各項：  
  
-   您可以透過瀏覽器存取接收位置嗎？ 如果您嘗試重新提交到 WCF 上手或 SOAP 上手，URL 應該表單 http://localhost/ESB.OnRampServices.WCF/ProcessItinerary.svc 或 http://localhost/ESB.OnRampServices/ProcessItinerary.asmx。 如果您嘗試重新提交到 HTTP 接收位置，您可以使用網際網路瀏覽器，判斷是否接收位置是否運作正確將範例訊息附加到查詢字串，如下列範例所示。  
  
    ```  
    http://localhost/HTTPOnRamp/BTSHttpReceive.dll?<SampleMessage>Sample Message Content</SampleMessage>  
    ```  
  
-   確認 BizTalk HTTP 接收配接器已正確設定。