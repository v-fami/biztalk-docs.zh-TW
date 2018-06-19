---
title: 發行 （建立新的訊息） 的 MX 訊息執行個體檔案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7e6cdf4-b9db-42be-a92d-10a7471e2c2d
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4082174428f177905527d0c648b4d7ad000dde36
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "25963116"
---
# <a name="publishing-the-mx-message-instance-file-creating-new-messages"></a><span data-ttu-id="aa581-102">發行 MX 訊息執行個體檔案 （建立新的訊息）</span><span class="sxs-lookup"><span data-stu-id="aa581-102">Publishing the MX Message Instance File (Creating New Messages)</span></span>
<span data-ttu-id="aa581-103">**若要發行的 MX 訊息執行個體檔案：**</span><span class="sxs-lookup"><span data-stu-id="aa581-103">**To publish the MX message instance file:**</span></span>  
  
1.  <span data-ttu-id="aa581-104">移至輸出資料夾的 InfoPath 表單範本，在上一個步驟中產生 **...\\< MessageType\>\TemplateDS\InfoPath 表單範本**。</span><span class="sxs-lookup"><span data-stu-id="aa581-104">Go to output folder of the InfoPath form template generated in the previous step **..\\<MessageType\>\TemplateDS\InfoPath Form Template**.</span></span>  
  
2.  <span data-ttu-id="aa581-105">在 Internet Explorer 中，開啟**http://localhost/sites/BASSite/New%20SWIFT%20MX%20Messages**。</span><span class="sxs-lookup"><span data-stu-id="aa581-105">In Internet Explorer, open **http://localhost/sites/BASSite/New%20SWIFT%20MX%20Messages**.</span></span>  
  
3.  <span data-ttu-id="aa581-106">在新的 Swift MX 訊息視窗中，按一下 **上傳**。</span><span class="sxs-lookup"><span data-stu-id="aa581-106">In New Swift MX Messages window, click **Upload**.</span></span>  
  
4.  <span data-ttu-id="aa581-107">在上傳文件視窗中，按一下 **瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="aa581-107">In the Upload Document window, click **Browse**.</span></span>  
  
5.  <span data-ttu-id="aa581-108">在 [選擇檔案] 對話方塊中，移至輸出資料夾的 InfoPath 表單上一個步驟中產生 **...\\< MessageType\>\TemplateDS\InfoPath 表單範本**。</span><span class="sxs-lookup"><span data-stu-id="aa581-108">In the Choose file dialog box, move to the output folder of the InfoPath form generated in the previous step **..\\<MessageType\>\TemplateDS\InfoPath Form Template**.</span></span> <span data-ttu-id="aa581-109">選取\<MessageType\>.xml 檔案 pacs.004.001.01.xml，例如，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="aa581-109">Select the \<MessageType\>.xml file such as pacs.004.001.01.xml, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="aa581-110">在上傳文件視窗中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="aa581-110">In the Upload Document window, click **OK**.</span></span>  
  
7.  <span data-ttu-id="aa581-111">新增 MX SWIFT 訊息中： \<MessageType\>視窗中的，於命名空間中，輸入 **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMX_ \<MessageType\>**，然後按一下 **確定**.</span><span class="sxs-lookup"><span data-stu-id="aa581-111">In the New SWIFT MX Messages: \<MessageType\> window, in the Namespace box, type **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMX_\<MessageType\>**, and then click **OK**.</span></span>