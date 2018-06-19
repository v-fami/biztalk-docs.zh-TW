---
title: JMS MQRFH2 範例相依性和強式金鑰名稱的定義 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a3a5cdce-dcdf-48df-91a5-8cf2afce9255
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f3e2f76a972f851322f82f2e89b285db907d799
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25976492"
---
# <a name="jms-mqrfh2-sample-dependencies-and-strong-key-name-definition"></a><span data-ttu-id="ac3f7-102">JMS MQRFH2 範例相依性和強式金鑰名稱定義</span><span class="sxs-lookup"><span data-stu-id="ac3f7-102">JMS MQRFH2 Sample Dependencies and Strong Key Name Definition</span></span>
<span data-ttu-id="ac3f7-103">ESB Visual Studio 專案。JMS。PipelineComponents 取決於下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="ac3f7-103">The Visual Studio project ESB.JMS.PipelineComponents depends on the following folder:</span></span>  
  
-   <span data-ttu-id="ac3f7-104">\<BizTalk Server 安裝目錄\>。</span><span class="sxs-lookup"><span data-stu-id="ac3f7-104">\<BizTalk Server Installation Directory\>.</span></span> <span data-ttu-id="ac3f7-105">這個資料夾可提供下列命名空間的存取：</span><span class="sxs-lookup"><span data-stu-id="ac3f7-105">This folder provides access to the following namespaces:</span></span>  
  
    -   <span data-ttu-id="ac3f7-106">**Microsoft::BizTalk::Message::Interop**</span><span class="sxs-lookup"><span data-stu-id="ac3f7-106">**Microsoft::BizTalk::Message::Interop**</span></span>  
  
    -   <span data-ttu-id="ac3f7-107">**Microsoft::BizTalk::Component::Interop**</span><span class="sxs-lookup"><span data-stu-id="ac3f7-107">**Microsoft::BizTalk::Component::Interop**</span></span>  
  
## <a name="the-strong-name-key-definition"></a><span data-ttu-id="ac3f7-108">強式名稱金鑰定義</span><span class="sxs-lookup"><span data-stu-id="ac3f7-108">The Strong Name Key Definition</span></span>  
 <span data-ttu-id="ac3f7-109">通常，強式名稱的索引鍵定義位於 AssemblyInfo.cpp 檔案中。</span><span class="sxs-lookup"><span data-stu-id="ac3f7-109">Usually, the strong-name key definition resides in the AssemblyInfo.cpp file.</span></span> <span data-ttu-id="ac3f7-110">不過，這會與 c + + 資訊清單檔案，之後會讀取 AssemblyInfo.cpp 檔案，編譯器會加入至組件的衝突。</span><span class="sxs-lookup"><span data-stu-id="ac3f7-110">However, this would conflict with the C++ manifest file that the compiler adds to the assembly after it reads the AssemblyInfo.cpp file.</span></span> <span data-ttu-id="ac3f7-111">這項衝突會讓任何嘗試將檔案放在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="ac3f7-111">This conflict would prevent any attempt to place the file in the global assembly cache.</span></span> <span data-ttu-id="ac3f7-112">不過，連結器會藉由指定金鑰檔位於控制強式名稱金鑰檔.../../../../../../ Keys/Microsoft.Practices.ESB.snk。</span><span class="sxs-lookup"><span data-stu-id="ac3f7-112">Instead, the linker controls the strong name key file by specifying the key file located at ../../../../../../Keys/Microsoft.Practices.ESB.snk.</span></span> <span data-ttu-id="ac3f7-113">若要編輯這個值，瀏覽至下列選項設定：</span><span class="sxs-lookup"><span data-stu-id="ac3f7-113">To edit this value, navigate to the following option setting:</span></span>  
  
 <span data-ttu-id="ac3f7-114">ESB。JMS。結構描述</span><span class="sxs-lookup"><span data-stu-id="ac3f7-114">ESB.JMS.Schemas</span></span>  
  
 <span data-ttu-id="ac3f7-115">\- 專案</span><span class="sxs-lookup"><span data-stu-id="ac3f7-115">\- Project</span></span>  
  
 <span data-ttu-id="ac3f7-116">\--內容</span><span class="sxs-lookup"><span data-stu-id="ac3f7-116">\- - Properties</span></span>  
  
 <span data-ttu-id="ac3f7-117">\---組態屬性</span><span class="sxs-lookup"><span data-stu-id="ac3f7-117">\- - - Configuration Properties</span></span>  
  
 <span data-ttu-id="ac3f7-118">\----連結器</span><span class="sxs-lookup"><span data-stu-id="ac3f7-118">\- - - - Linker</span></span>  
  
 <span data-ttu-id="ac3f7-119">\-----進階</span><span class="sxs-lookup"><span data-stu-id="ac3f7-119">\- - - - - Advanced</span></span>  
  
 <span data-ttu-id="ac3f7-120">\------金鑰檔</span><span class="sxs-lookup"><span data-stu-id="ac3f7-120">\- - - - - - Key File</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac3f7-121">如果您建構 JMS 管線元件，您必須編輯 AssemblyInfo.cpp 檔案，移除任何參考強式名稱金鑰檔，如先前所述。</span><span class="sxs-lookup"><span data-stu-id="ac3f7-121">If you construct a JMS Pipeline Component, you must edit the AssemblyInfo.cpp file to remove any references to the strong-name key file, as described earlier.</span></span> <span data-ttu-id="ac3f7-122">這麼做之後，編輯**金鑰檔案**選項的連結器的進階屬性中指定的路徑和強式名稱金鑰檔名稱。</span><span class="sxs-lookup"><span data-stu-id="ac3f7-122">After you do that, edit the **Key File** option in the advanced properties of the Linker to specify the path and name of the strong-name key file.</span></span>