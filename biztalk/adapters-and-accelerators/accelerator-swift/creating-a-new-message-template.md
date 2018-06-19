---
title: 建立新的郵件範本 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, templates
- templates, creating
- creating, templates
ms.assetid: 8c601d2b-b7a5-4ac4-9d98-fd9960038340
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a15e1c2a59635ca653e5a4817f29cdc918dca09
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209238"
---
# <a name="creating-a-new-message-template"></a><span data-ttu-id="b2065-102">建立新的郵件範本</span><span class="sxs-lookup"><span data-stu-id="b2065-102">Creating a New Message Template</span></span>
<span data-ttu-id="b2065-103">您可以從現有的範本建立新的郵件範本。</span><span class="sxs-lookup"><span data-stu-id="b2065-103">You can create a new message template from an existing template.</span></span> <span data-ttu-id="b2065-104">這可讓自訂的表單，例如標準的 SWIFT 表單已輸入一些資料的複本上建立新的訊息執行個體的建立者。</span><span class="sxs-lookup"><span data-stu-id="b2065-104">This enables a creator to create a new message instance on a custom form, such as a copy of a standard SWIFT form that already has some data entered into it.</span></span> <span data-ttu-id="b2065-105">使用新範本，建立者並沒有輸入的所有使用空的表單時所需的資料。</span><span class="sxs-lookup"><span data-stu-id="b2065-105">Using the new template, the creator does not have to enter all of the data required when using an empty form.</span></span>  
  
 <span data-ttu-id="b2065-106">從您已經使用對應的現有範本來產生訊息執行個體建立新的範本。</span><span class="sxs-lookup"><span data-stu-id="b2065-106">You create a new template from a message instance that you have generated using the corresponding existing template.</span></span> <span data-ttu-id="b2065-107">您將資料的欄位加入[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成 （如同您所建立的新訊息執行個體），並為新範本儲存表單。</span><span class="sxs-lookup"><span data-stu-id="b2065-107">You add data to the fields of the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form (as though you were creating a new message instance), and then save the form as a new template.</span></span>  
  
### <a name="to-save-a-modified-existing-template-as-a-new-template"></a><span data-ttu-id="b2065-108">若要儲存已修改現有的範本作為新範本</span><span class="sxs-lookup"><span data-stu-id="b2065-108">To save a modified existing template as a new template</span></span>  
  
1.  <span data-ttu-id="b2065-109">在 Internet Explorer 中，開啟 MRSR http://localhost/sites/bassite 您的網站。</span><span class="sxs-lookup"><span data-stu-id="b2065-109">In Internet Explorer, open your MRSR site at http://localhost/sites/bassite.</span></span>  
  
2.  <span data-ttu-id="b2065-110">按一下**文件**。</span><span class="sxs-lookup"><span data-stu-id="b2065-110">Click **Documents**.</span></span>  
  
3.  <span data-ttu-id="b2065-111">在文件] 頁面上，按一下 [**新 SWIFT MT 訊息**文件庫。</span><span class="sxs-lookup"><span data-stu-id="b2065-111">On the Documents page, click the **New SWIFT MT Messages** document library.</span></span>  
  
4.  <span data-ttu-id="b2065-112">在新的 SWIFT MT 訊息 頁面上，按一下包含您想要根據您的新範本的範本類別。</span><span class="sxs-lookup"><span data-stu-id="b2065-112">On the New SWIFT MT Messages page, click the category containing the template that you want to base your new template on.</span></span>  
  
5.  <span data-ttu-id="b2065-113">指向您想要根據您的新範本，按一下向右箭號，然後按一下範本**編輯在 Microsoft Office InfoPath**。</span><span class="sxs-lookup"><span data-stu-id="b2065-113">Point to the template that you want to base your new template on, click the arrow to the right, and then click **Edit in Microsoft Office InfoPath**.</span></span>  
  
6.  <span data-ttu-id="b2065-114">在[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]2007年 視窗中，在 [郵件] 表單中，輸入您想要範本的一部分的訊息資料。</span><span class="sxs-lookup"><span data-stu-id="b2065-114">In the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window, in the message form, enter message data that you want to be part of the template.</span></span>  
  
7.  <span data-ttu-id="b2065-115">按一下**檔案**，然後按一下**存**。</span><span class="sxs-lookup"><span data-stu-id="b2065-115">Click **File**, and then click **Save As**.</span></span>  
  
8.  <span data-ttu-id="b2065-116">快顯視窗指出，表單包含驗證錯誤，請按一下**是**。</span><span class="sxs-lookup"><span data-stu-id="b2065-116">In the popup indicating that the form contains validation errors, click **Yes**.</span></span>  
  
9. <span data-ttu-id="b2065-117">在 另存新檔 對話方塊中，選取 在範本資料夾**存**文字，然後再輸入中的檔案名稱**檔案名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="b2065-117">In the Save As dialog box, select the folder for the template in the **Save in** text box, and then enter a file name in the **File name** text box.</span></span> <span data-ttu-id="b2065-118">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="b2065-118">Click **Save**.</span></span>  
  
10. <span data-ttu-id="b2065-119">關閉[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]新範本的表單。</span><span class="sxs-lookup"><span data-stu-id="b2065-119">Close the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form for the new template.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b2065-120">若要從新的範本建立訊息執行個體，請參閱[建立及提交新訊息](../../adapters-and-accelerators/accelerator-swift/creating-and-submitting-a-new-message.md)。</span><span class="sxs-lookup"><span data-stu-id="b2065-120">To create a message instance from the new template, see [Creating and Submitting a New Message](../../adapters-and-accelerators/accelerator-swift/creating-and-submitting-a-new-message.md).</span></span>