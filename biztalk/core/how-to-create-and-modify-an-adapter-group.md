---
title: "如何建立和修改配接器群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1eef051-2ed7-4e28-8cb9-0145d6c8ed76
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6865de8eb67d9fe1a6ca8d93b7d2e6527ae36364
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-and-modify-an-adapter-group"></a><span data-ttu-id="1fae5-102">如何建立和修改配接器群組</span><span class="sxs-lookup"><span data-stu-id="1fae5-102">How to Create and Modify an Adapter Group</span></span>
<span data-ttu-id="1fae5-103">單一登入 (SSO) 的其中一項新功能是能夠建立和修改配接器群組。</span><span class="sxs-lookup"><span data-stu-id="1fae5-103">One of the new features of Single Sign-On (SSO) is the ability to create and modify adapter groups.</span></span> <span data-ttu-id="1fae5-104">配接器群組正如其名，就是配接器的組合。</span><span class="sxs-lookup"><span data-stu-id="1fae5-104">As the name implies, an adapter group is a collection of adapters.</span></span> <span data-ttu-id="1fae5-105">您可以使用配接器群組來組織配接器的安全性設定及其他屬性。</span><span class="sxs-lookup"><span data-stu-id="1fae5-105">You can use adapter groups to organize security settings and other properties for your adapters.</span></span>  
  
### <a name="to-create-and-modify-an-adapter-group"></a><span data-ttu-id="1fae5-106">若要建立和修改配接器群組</span><span class="sxs-lookup"><span data-stu-id="1fae5-106">To create and modify an adapter group</span></span>  
  
1.  <span data-ttu-id="1fae5-107">使用 SSOPS 工具的呼叫來建立配接器群組。</span><span class="sxs-lookup"><span data-stu-id="1fae5-107">Create the adapter group by using a call to the ssops tool.</span></span>  
  
     <span data-ttu-id="1fae5-108">在關聯的 XML 檔案中，必須將群組旗標設定為配接器群組。</span><span class="sxs-lookup"><span data-stu-id="1fae5-108">In the associated XML file, you must set the group flag as an adapter group.</span></span>  
  
2.  <span data-ttu-id="1fae5-109">使用 `ISSOPSAdmin.AddAdapterToAdapterGroup` 新增一或多個配接器到配接器群組。</span><span class="sxs-lookup"><span data-stu-id="1fae5-109">Add one or more adapters to the adapter group by using `ISSOPSAdmin.AddAdapterToAdapterGroup`.</span></span>  
  
     <span data-ttu-id="1fae5-110">此時，配接器群組已準備就緒可供使用。</span><span class="sxs-lookup"><span data-stu-id="1fae5-110">At this point, your adapter group is ready to work as intended.</span></span> <span data-ttu-id="1fae5-111">如有必要，可使用 `ISSOPSAdmin.GetAdaptersForAdapterGroup` 檢視關聯配接器的完整清單。</span><span class="sxs-lookup"><span data-stu-id="1fae5-111">If necessary, you can view the full list of associated adapters by using `ISSOPSAdmin.GetAdaptersForAdapterGroup`.</span></span>  
  
3.  <span data-ttu-id="1fae5-112">您可以使用 `ISSOPSAdmin.SetAdapterProperties` 修改配接器群組的設定。</span><span class="sxs-lookup"><span data-stu-id="1fae5-112">You can modify the settings of your adapter group using `ISSOPSAdmin.SetAdapterProperties`.</span></span>  
  
4.  <span data-ttu-id="1fae5-113">完成後，就可以使用 `ISSOPSAdmin.RemoveAdapterFromAdapterGroup` 從配接器群組中移除配接器。</span><span class="sxs-lookup"><span data-stu-id="1fae5-113">When you are finished, you can remove the adapter from the adapter group using `ISSOPSAdmin.RemoveAdapterFromAdapterGroup`.</span></span>  
  
5.  <span data-ttu-id="1fae5-114">最後，您可以使用 `ISSOAdmin.DeleteApplication` 刪除配接器群組。</span><span class="sxs-lookup"><span data-stu-id="1fae5-114">Finally, you can delete the adapter group by using `ISSOAdmin.DeleteApplication`.</span></span>  
  
     <span data-ttu-id="1fae5-115">或者，可以改用 SSOPS 工具的 `-delete` 命令刪除配接器群組。</span><span class="sxs-lookup"><span data-stu-id="1fae5-115">You may choose instead to delete the adapter group by using the `-delete` command of the ssops tool.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fae5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fae5-116">See Also</span></span>  
 [<span data-ttu-id="1fae5-117">同步處理密碼</span><span class="sxs-lookup"><span data-stu-id="1fae5-117">Synchronizing Passwords</span></span>](../core/synchronizing-passwords.md)