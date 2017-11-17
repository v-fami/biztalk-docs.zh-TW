---
title: "錯誤 Messages1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: error messages
ms.assetid: db9c9634-3f4b-4b38-b3ba-388e587fccd8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80a44049c43c499ac05a8a6f296d11add934267a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error-messages"></a><span data-ttu-id="30080-102">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="30080-102">Error Messages</span></span>
<span data-ttu-id="30080-103">下表說明 JD Edwards EnterpriseOne 系統中的錯誤訊息並提供可能的更正方式。</span><span class="sxs-lookup"><span data-stu-id="30080-103">The following table describes error messages in the JD Edwards EnterpriseOne system and provides possible corrections for them.</span></span>  
  
|<span data-ttu-id="30080-104">錯誤識別碼</span><span class="sxs-lookup"><span data-stu-id="30080-104">Error ID</span></span>|<span data-ttu-id="30080-105">可能的原因 / 錯誤描述</span><span class="sxs-lookup"><span data-stu-id="30080-105">Possible Cause / Error Description</span></span>|<span data-ttu-id="30080-106">可能的更正方式</span><span class="sxs-lookup"><span data-stu-id="30080-106">Possible Correction</span></span>|  
|--------------|-----------------------------------------|-------------------------|  
|<span data-ttu-id="30080-107">E-JDE0027</span><span class="sxs-lookup"><span data-stu-id="30080-107">E-JDE0027</span></span>|<span data-ttu-id="30080-108">遺失 JD Edwards EnterpriseOne JAR 檔案。</span><span class="sxs-lookup"><span data-stu-id="30080-108">JD Edwards EnterpriseOne JAR files missing.</span></span> <span data-ttu-id="30080-109">無法取得 JD Edwards EnterpriseOne 連線物件。</span><span class="sxs-lookup"><span data-stu-id="30080-109">Unable to acquire JD Edwards EnterpriseOne connection object.</span></span>|<span data-ttu-id="30080-110">確認您的認證。</span><span class="sxs-lookup"><span data-stu-id="30080-110">Verify your credentials.</span></span> <span data-ttu-id="30080-111">確認您的 CLASSPATH 設定和登入認證。</span><span class="sxs-lookup"><span data-stu-id="30080-111">Verify your CLASSPATH settings and logon credentials.</span></span> <span data-ttu-id="30080-112">請參閱環境變數。</span><span class="sxs-lookup"><span data-stu-id="30080-112">Refer to Environment variable.</span></span>|  
|<span data-ttu-id="30080-113">I-JDE0043</span><span class="sxs-lookup"><span data-stu-id="30080-113">I-JDE0043</span></span>|<span data-ttu-id="30080-114">錯誤的應用程式伺服器、連接埠、環境、組態檔路徑、使用者、密碼。</span><span class="sxs-lookup"><span data-stu-id="30080-114">Wrong App Server, Port, Environment, Path for Configuration File, User, Password.</span></span> <span data-ttu-id="30080-115">登入失敗。</span><span class="sxs-lookup"><span data-stu-id="30080-115">Log in failed.</span></span>|<span data-ttu-id="30080-116">確認您的登入認證。</span><span class="sxs-lookup"><span data-stu-id="30080-116">Verify your log in credentials.</span></span> <span data-ttu-id="30080-117">請參閱環境變數。</span><span class="sxs-lookup"><span data-stu-id="30080-117">Refer to Environment variable.</span></span>|  
|<span data-ttu-id="30080-118">I-JDE0048</span><span class="sxs-lookup"><span data-stu-id="30080-118">I-JDE0048</span></span>|<span data-ttu-id="30080-119">如果 jdearglist.txt 檔案不存在或內容空白，記錄檔中就會在 Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 開啟時出現一則資訊訊息。</span><span class="sxs-lookup"><span data-stu-id="30080-119">If the jdearglist.txt file does not exist or is empty, an informational message appears in the log when Microsoft BizTalk Adapter for JD Edwards EnterpriseOne opens.</span></span>|<span data-ttu-id="30080-120">更新 jdearglist.txt 檔案以輸入參數的清單，使參數自動靠右對齊並在左側填滿空格。</span><span class="sxs-lookup"><span data-stu-id="30080-120">Update the jdearglist.txt file to enter a list of parameters so that they are automatically right justified and padded on the left with blanks.</span></span> <span data-ttu-id="30080-121">如需詳細資訊，請參閱[處理字串值](../core/handling-string-values2.md)。</span><span class="sxs-lookup"><span data-stu-id="30080-121">For more information, see  [Handling String Values](../core/handling-string-values2.md).</span></span> <span data-ttu-id="30080-122">您每次變更 jdearglist，就必須重新產生該商務物件的結構描述。</span><span class="sxs-lookup"><span data-stu-id="30080-122">Every time you change the jdearglist, you must regenerate the schemas for that business object.</span></span>|  
|<span data-ttu-id="30080-123">E-JDE0027</span><span class="sxs-lookup"><span data-stu-id="30080-123">E-JDE0027</span></span>|<span data-ttu-id="30080-124">無法取得 JD Edwards EnterpriseOne 連線物件。</span><span class="sxs-lookup"><span data-stu-id="30080-124">Unable to acquire JD Edwards EnterpriseOne connection object.</span></span> <span data-ttu-id="30080-125">請檢查您的 CLASSPATH 和認證。</span><span class="sxs-lookup"><span data-stu-id="30080-125">Please check your CLASSPATH and credentials.</span></span>|<span data-ttu-id="30080-126">確認 jdeinterop.ini 位置。</span><span class="sxs-lookup"><span data-stu-id="30080-126">Verify the location of jdeinterop.ini.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30080-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30080-127">See Also</span></span>  
 <span data-ttu-id="30080-128">[疑難排解 JD Edwards EnterpriseOne](../core/troubleshooting-jd-edwards-enterpriseone.md) </span><span class="sxs-lookup"><span data-stu-id="30080-128">[Troubleshooting JD Edwards EnterpriseOne](../core/troubleshooting-jd-edwards-enterpriseone.md) </span></span>  
 [<span data-ttu-id="30080-129">技術參考</span><span class="sxs-lookup"><span data-stu-id="30080-129">Technical Reference</span></span>](../core/technical-reference6.md)