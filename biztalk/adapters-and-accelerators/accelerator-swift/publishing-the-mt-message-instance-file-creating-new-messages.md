---
title: 發行 （建立新的訊息） 的 MT 訊息執行個體檔案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52118d20-f325-432a-9e3e-5cc10232cba0
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00ae6aabf2a51071d1dfe078914bc92487a6505e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22213950"
---
# <a name="publishing-the-mt-message-instance-file-creating-new-messages"></a><span data-ttu-id="32f4c-102">發行 （建立新的訊息） 的 MT 訊息執行個體檔案</span><span class="sxs-lookup"><span data-stu-id="32f4c-102">Publishing the MT Message Instance File (Creating New Messages)</span></span>
<span data-ttu-id="32f4c-103">**若要發行的 MT 訊息執行個體檔案：**</span><span class="sxs-lookup"><span data-stu-id="32f4c-103">**To publish the MT message instance file:**</span></span>  
  
1.  <span data-ttu-id="32f4c-104">移至輸出資料夾的 InfoPath 表單範本，在上一個步驟中產生 **...\MTXXX\TemplateDS\InfoPath 表單範本**。</span><span class="sxs-lookup"><span data-stu-id="32f4c-104">Go to output folder of the InfoPath form template generated in the previous step **..\MTXXX\TemplateDS\InfoPath Form Template**.</span></span>  
  
2.  <span data-ttu-id="32f4c-105">在 Internet Explorer 中，開啟**http://localhost/sites/BASSite/New%20SWIFT%20MT%20Messages**。</span><span class="sxs-lookup"><span data-stu-id="32f4c-105">In Internet Explorer, open **http://localhost/sites/BASSite/New%20SWIFT%20MT%20Messages**.</span></span>  
  
3.  <span data-ttu-id="32f4c-106">在新的 Swift MT 訊息視窗中，按一下 **上傳**。</span><span class="sxs-lookup"><span data-stu-id="32f4c-106">In New Swift MT Messages window, click **Upload**.</span></span>  
  
4.  <span data-ttu-id="32f4c-107">在上傳文件視窗中，按一下 **瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="32f4c-107">In the Upload Document window, click **Browse**.</span></span>  
  
5.  <span data-ttu-id="32f4c-108">在 [選擇檔案] 對話方塊中，移至輸出資料夾的 InfoPath 表單上一個步驟中產生 **...\MTXXX\TemplateDS\InfoPath 表單範本**。</span><span class="sxs-lookup"><span data-stu-id="32f4c-108">In the Choose file dialog box, move to the output folder of the InfoPath form generated in the previous step **..\MTXXX\TemplateDS\InfoPath Form Template**.</span></span> <span data-ttu-id="32f4c-109">選取例如 MT103.xml MTXXX.xml 檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="32f4c-109">Select the MTXXX.xml file such as MT103.xml and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="32f4c-110">在上傳文件視窗中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="32f4c-110">In the Upload Document window, click **OK**.</span></span>  
  
7.  <span data-ttu-id="32f4c-111">在新的 SWIFT MT 郵件中： MTXXX 視窗中的，於命名空間中，輸入**http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMTxxx**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="32f4c-111">In the New SWIFT MT Messages: MTXXX window, in the Namespace box, type **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMTxxx**, and then click **OK**.</span></span>