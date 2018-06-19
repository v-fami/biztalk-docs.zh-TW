---
title: 使用連結指定記錄和欄位對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1c669d93-e088-459e-8f45-87c359874a7e
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a79595e3acc916e61919d77c4f39fe24ff43b00f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287246"
---
# <a name="using-links-to-specify-record-and-field-mappings"></a><span data-ttu-id="fa9e3-102">使用連結指定記錄和欄位對應</span><span class="sxs-lookup"><span data-stu-id="fa9e3-102">Using Links to Specify Record and Field Mappings</span></span>
<span data-ttu-id="fa9e3-103">在 BizTalk 對應工具中，連結是一種將來源結構描述中的資料項目與目的結構描述中的資料項目產生關聯的方法。</span><span class="sxs-lookup"><span data-stu-id="fa9e3-103">In BizTalk Mapper, a link is the way you associate a data item in the source schema with a data item in the destination schema.</span></span> <span data-ttu-id="fa9e3-104">通常在完成的對應中，來源結構描述與目的結構描述之間會有多個連結。</span><span class="sxs-lookup"><span data-stu-id="fa9e3-104">Typically, in a completed map there are many links between the source schema and the destination schema.</span></span> <span data-ttu-id="fa9e3-105">整體而言，這些連結指定來源執行個體訊息中的資料如何轉換至語意相同、但語法不同的目的執行個體訊息中。</span><span class="sxs-lookup"><span data-stu-id="fa9e3-105">All together the links specify how the data in the source instance messages will be transformed into a semantically equivalent, but syntactically distinct, destination instance messages.</span></span>  
  
 <span data-ttu-id="fa9e3-106">本節提供建立新連結、使用現有連結、自動建立連結，以及其他連結作業的工作特定資訊。</span><span class="sxs-lookup"><span data-stu-id="fa9e3-106">This section provides task-specific information about creating new links, working with existing links, creating links automatically, and other linking operations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa9e3-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="fa9e3-107">In This Section</span></span>  
  
-   [<span data-ttu-id="fa9e3-108">如何建立連結</span><span class="sxs-lookup"><span data-stu-id="fa9e3-108">How to Create Links</span></span>](../core/how-to-create-links.md)  
  
-   [<span data-ttu-id="fa9e3-109">如何編輯連結屬性</span><span class="sxs-lookup"><span data-stu-id="fa9e3-109">How to Edit Link Properties</span></span>](../core/how-to-edit-link-properties.md)  
  
-   [<span data-ttu-id="fa9e3-110">如何自動連結記錄</span><span class="sxs-lookup"><span data-stu-id="fa9e3-110">How to Link Records Automatically</span></span>](../core/how-to-link-records-automatically.md)  
  
-   [<span data-ttu-id="fa9e3-111">如何管理現有的連結</span><span class="sxs-lookup"><span data-stu-id="fa9e3-111">How to Manage Existing Links</span></span>](../core/how-to-manage-existing-links.md)  
  
-   [<span data-ttu-id="fa9e3-112">如何設定節點階層比對</span><span class="sxs-lookup"><span data-stu-id="fa9e3-112">How to Configure Node Hierarchy Matching</span></span>](../core/how-to-configure-node-hierarchy-matching.md)  
  
-   [<span data-ttu-id="fa9e3-113">如何設定來源連結編譯器值</span><span class="sxs-lookup"><span data-stu-id="fa9e3-113">How to Set the Source Links Compiler Value</span></span>](../core/how-to-set-the-source-links-compiler-value.md)  
  
-   [<span data-ttu-id="fa9e3-114">如何顯示和隱藏編譯器連結</span><span class="sxs-lookup"><span data-stu-id="fa9e3-114">How to Show and Hide Compiler Links</span></span>](../core/how-to-show-and-hide-compiler-links.md)  
  
-   [<span data-ttu-id="fa9e3-115">如何複製、 剪下、 貼上連結和運算質</span><span class="sxs-lookup"><span data-stu-id="fa9e3-115">How to Copy, Cut, and Paste Links and Functoids</span></span>](../core/how-to-copy-cut-and-paste-links-and-functoids.md)  
  
-   [<span data-ttu-id="fa9e3-116">如何標示連結</span><span class="sxs-lookup"><span data-stu-id="fa9e3-116">How to Label a Link</span></span>](../core/how-to-label-a-link.md)  
  
-   [<span data-ttu-id="fa9e3-117">如何選取多個連結與運算質</span><span class="sxs-lookup"><span data-stu-id="fa9e3-117">How to Select Multiple Links and Functoids</span></span>](../core/how-to-select-multiple-links-and-functoids.md)  
  
-   [<span data-ttu-id="fa9e3-118">如何在多個連結與運算質設定標籤和註解</span><span class="sxs-lookup"><span data-stu-id="fa9e3-118">How to Set Label and Comment on Multiple Links and Functoids</span></span>](../core/how-to-set-label-and-comment-on-multiple-links-and-functoids.md)