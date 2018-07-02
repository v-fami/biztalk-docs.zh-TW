---
title: 在來源中的空節點值執行個體訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76f9d7c8-5a82-41e9-9077-7b1ddd80a837
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d847aace487d7b7ebd472ec96173e38315df529
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976615"
---
# <a name="empty-node-values-in-source-instance-messages"></a><span data-ttu-id="7f66d-102">來源執行個體訊息中的空節點值</span><span class="sxs-lookup"><span data-stu-id="7f66d-102">Empty Node Values in Source Instance Messages</span></span>
<span data-ttu-id="7f66d-103">當您測試對應時，有時可能不想要所有結構描述節點的內容。</span><span class="sxs-lookup"><span data-stu-id="7f66d-103">There may be times when you do not want content in all of the schema nodes when you test a map.</span></span>  

## <a name="ceate-empty-node-values"></a><span data-ttu-id="7f66d-104">建立空節點值</span><span class="sxs-lookup"><span data-stu-id="7f66d-104">Ceate empty node values</span></span>  

1. <span data-ttu-id="7f66d-105">使用 BizTalk 總管產生執行個體資料。</span><span class="sxs-lookup"><span data-stu-id="7f66d-105">Generate instance data using BizTalk Editor.</span></span> <span data-ttu-id="7f66d-106">如需有關產生執行個體資料的詳細資訊，請參閱[如何產生執行個體訊息](../core/how-to-generate-instance-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="7f66d-106">For more information about generating instance data, see [How to Generate Instance Messages](../core/how-to-generate-instance-messages.md).</span></span>  

2. <span data-ttu-id="7f66d-107">在文字編輯器中開啟輸入執行個體訊息，刪除您想要變空白的項目和屬性的資料，然後儲存已修改的執行個體檔案。</span><span class="sxs-lookup"><span data-stu-id="7f66d-107">Open the input instance message in a text editor, delete the data from elements and attributes that you want to be empty, and then save the modified instance file.</span></span>  

3. <span data-ttu-id="7f66d-108">當結構描述已驗證和已測試時，設定 BizTalk 對應工具以使用剛才修改的檔案。</span><span class="sxs-lookup"><span data-stu-id="7f66d-108">Configure BizTalk Mapper to use the file you just modified when the schema is validated and tested.</span></span> <span data-ttu-id="7f66d-109">您在結構描述的 [屬性] 視窗設定檔案。</span><span class="sxs-lookup"><span data-stu-id="7f66d-109">You set the file in the Properties window for the schema.</span></span> <span data-ttu-id="7f66d-110">如需有關設定屬性的詳細資訊，請參閱 <<c0>  **對應檔屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="7f66d-110">For more information about setting properties, see **Map File Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="7f66d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f66d-111">See Also</span></span>  
- [<span data-ttu-id="7f66d-112">如何產生執行個體訊息</span><span class="sxs-lookup"><span data-stu-id="7f66d-112">How to Generate Instance Messages</span></span>](../core/how-to-generate-instance-messages.md)   
- <span data-ttu-id="7f66d-113">**結構描述屬性參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="7f66d-113">**Schema Property Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
