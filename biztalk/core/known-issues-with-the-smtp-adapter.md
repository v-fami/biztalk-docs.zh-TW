---
title: "SMTP 配接器的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b530e39e-c4e7-4b98-be0b-4d02eb2e8dc7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8691da466c2915cee4b8746e20a0d5a96d82d81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-smtp-adapter"></a><span data-ttu-id="0f649-102">SMTP 配接器的已知問題</span><span class="sxs-lookup"><span data-stu-id="0f649-102">Known Issues with the SMTP Adapter</span></span>
<span data-ttu-id="0f649-103">本節包含可幫助您避免錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="0f649-103">This section contains information that may help you avoid errors.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="0f649-104">已知問題</span><span class="sxs-lookup"><span data-stu-id="0f649-104">Known Issues</span></span>  
  
#### <a name="error-in-the-biztalk-server-application-log-if-emailbodytextcharset-is-not-defined"></a><span data-ttu-id="0f649-105">如果未定義 EmailBodyTextCharset，會在 BizTalk Server 應用程式記錄檔中產生錯誤</span><span class="sxs-lookup"><span data-stu-id="0f649-105">Error in the BizTalk Server Application Log if EmailBodyTextCharset is not defined</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="0f649-106">問題</span><span class="sxs-lookup"><span data-stu-id="0f649-106">Problem</span></span>  
 <span data-ttu-id="0f649-107">如果未定義 EmailBodyTextCharset，會在 BizTalk Server 應用程式記錄檔中產生錯誤，並在 BizTalk Server 應用程式記錄檔中產生類似下列的錯誤：</span><span class="sxs-lookup"><span data-stu-id="0f649-107">Errors are generated in the BizTalk Server application log if the EmailBodyTextCharset is not defined and an error similar to the followign is generated in the BizTalk Server application log:</span></span>  
  
```  
Event Type:Error  
Event Source:BizTalk Server 2009  
Event Category:BizTalk Server 2009   
Event ID:5754  
Date:9/1/2006  
Time:10:50:11 AM  
User:N/A  
Computer:TEST2006  
Description:  
A message sent to adapter "SMTP" on send port "TIE Test_1.0.0.0_TIE_Test.TieRespTest_Email_Port_4f4f8f4101d5615a" with URI "mailto:approver@BTS2006.com" is suspended.   
Error details: Unknown Error Description   
MessageId: {3F12EBE1-1CDA-44FE-85FE-C2CB8228F287}  
InstanceID: {0616E750-22FF-4380-B413-C94718421340}  
```  
  
##### <a name="cause"></a><span data-ttu-id="0f649-108">原因</span><span class="sxs-lookup"><span data-stu-id="0f649-108">Cause</span></span>  
 <span data-ttu-id="0f649-109">值必須設定為**EmailBodyTextCharset**參數。</span><span class="sxs-lookup"><span data-stu-id="0f649-109">A value must be set for the **EmailBodyTextCharset** parameter.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="0f649-110">解決方案</span><span class="sxs-lookup"><span data-stu-id="0f649-110">Resolution</span></span>  
 <span data-ttu-id="0f649-111">指定的值**EmailBodyTextCharset**參數。</span><span class="sxs-lookup"><span data-stu-id="0f649-111">Specify a value for the **EmailBodyTextCharset** parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f649-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f649-112">See Also</span></span>  
 [<span data-ttu-id="0f649-113">SMTP 配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="0f649-113">Troubleshooting the SMTP Adapter</span></span>](../core/troubleshooting-the-smtp-adapter.md)