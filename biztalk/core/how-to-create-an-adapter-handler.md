---
title: 如何建立配接器處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, handlers [adapters]
- handlers [adapters], creating
- adapters, handlers
ms.assetid: 09569417-dce6-473d-891f-6fd12347bcf0
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e26caf02978006040e52ed3c62e520f51362e2c4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969860"
---
# <a name="how-to-create-an-adapter-handler"></a><span data-ttu-id="e7261-102">如何建立配接器處理常式</span><span class="sxs-lookup"><span data-stu-id="e7261-102">How to Create an Adapter Handler</span></span>
<span data-ttu-id="e7261-103">您可以使用 [BizTalk Server 管理] 主控台以建立傳送或接收配接器處理常式。</span><span class="sxs-lookup"><span data-stu-id="e7261-103">You can create a send or receive adapter handler by using the BizTalk Server Administration Console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7261-104">您必須是「單一登入系統管理員」群組的成員才能建立配接器處理常式。</span><span class="sxs-lookup"><span data-stu-id="e7261-104">You must be a member of the Single Sign-On Administrators group to create an adapter handler.</span></span>  
  
### <a name="to-create-an-adapter-handler"></a><span data-ttu-id="e7261-105">建立配接器處理常式</span><span class="sxs-lookup"><span data-stu-id="e7261-105">To create an adapter handler</span></span>  
  
1.  <span data-ttu-id="e7261-106">在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開  **配接器**。</span><span class="sxs-lookup"><span data-stu-id="e7261-106">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="e7261-107">在展開的配接器清單中，以滑鼠右鍵按一下配接器，您想要新增傳送或接收處理常式，請指向**新增**，然後按一下 **傳送處理常式**建立傳送處理常式，或按一下**接收處理常式**建立接收處理常式。</span><span class="sxs-lookup"><span data-stu-id="e7261-107">In the expanded adapter list, right-click the adapter for which you would like to add a send or receive handler, point to **New**, and then click **Send Handler** to create a send handler or click **Receive Handler** to create a receive handler.</span></span>  
  
3.  <span data-ttu-id="e7261-108">在**\<主機名稱\>屬性**對話方塊**一般**索引標籤的**主機名稱**清單中，選取與主機配接器處理常式將關聯。</span><span class="sxs-lookup"><span data-stu-id="e7261-108">In the **\<host name\> Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the adapter handler will be associated.</span></span>  
  
4.  <span data-ttu-id="e7261-109">如果您要建立的配接器傳送處理常式，選取 **設預設處理常式**如果您想要為此配接器的預設傳送處理常式。</span><span class="sxs-lookup"><span data-stu-id="e7261-109">If you are creating an adapter send handler, select the option to **Make this the default handler** if you would like for this to be the default send handler for this adapter.</span></span>  
  
5.  <span data-ttu-id="e7261-110">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="e7261-110">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7261-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="e7261-111">See Also</span></span>  
 [<span data-ttu-id="e7261-112">建立和刪除配接器處理常式</span><span class="sxs-lookup"><span data-stu-id="e7261-112">Creating and Deleting Adapter Handlers</span></span>](../core/creating-and-deleting-adapter-handlers.md)