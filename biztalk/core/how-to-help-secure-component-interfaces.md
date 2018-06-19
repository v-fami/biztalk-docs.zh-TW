---
title: 如何協助保護元件介面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- component interfaces, helping to secure
- security, component interfaces
ms.assetid: 03b2af44-78e7-4fdc-bfa3-7697b2a60986
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54136aaeae9578ae4e438c5bd8b95b902d618f96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255214"
---
# <a name="how-to-help-secure-component-interfaces"></a><span data-ttu-id="fd6f5-102">如何協助保護元件介面的安全</span><span class="sxs-lookup"><span data-stu-id="fd6f5-102">How to Help Secure Component Interfaces</span></span>
<span data-ttu-id="fd6f5-103">在您開始測試元件介面之前，必須先設定其安全性。</span><span class="sxs-lookup"><span data-stu-id="fd6f5-103">Before you can start testing a component interface, you must set up security for it.</span></span> <span data-ttu-id="fd6f5-104">下列程序描述如何設定 PeopleSoft 8.4 版，元件介面安全性，但您可以針對 8.1 版使用此程序。</span><span class="sxs-lookup"><span data-stu-id="fd6f5-104">The following procedure describes how to configure component interface security for PeopleSoft Version 8.4, but you can use the procedure for Version 8.1.</span></span>  
  
### <a name="to-configure-interface-security"></a><span data-ttu-id="fd6f5-105">若要設定介面安全性</span><span class="sxs-lookup"><span data-stu-id="fd6f5-105">To configure interface security</span></span>  
  
1.  <span data-ttu-id="fd6f5-106">展開**PeopleTools**，依序展開**安全性**，依序展開**使用者設定檔**，然後展開**Permissions & Roles**。</span><span class="sxs-lookup"><span data-stu-id="fd6f5-106">Expand **PeopleTools**, expand **Security**, expand **User Profiles**, and then expand **Permissions & Roles**.</span></span>  
  
     ![](../core/media/psadapter-47-ps-configsecurity1.gif "PSAdapter_47_PS_ConfigSecurity1")  
  
2.  <span data-ttu-id="fd6f5-107">按一下**權限清單**。</span><span class="sxs-lookup"><span data-stu-id="fd6f5-107">Click **Permission Lists**.</span></span>  
  
3.  <span data-ttu-id="fd6f5-108">按一下 **[搜尋]**。</span><span class="sxs-lookup"><span data-stu-id="fd6f5-108">Click **Search**.</span></span>  
  
     ![](../core/media/psadapter-48-ps-configsecurity2.gif "PSAdapter_48_PS_ConfigSecurity2")  
  
4.  <span data-ttu-id="fd6f5-109">在**Permission Lists Search**  窗格中，選取相關的權限清單。</span><span class="sxs-lookup"><span data-stu-id="fd6f5-109">In the **Permission Lists Search** pane, select the relevant permission list.</span></span>  
  
     <span data-ttu-id="fd6f5-110">此時就會顯示下列視窗。</span><span class="sxs-lookup"><span data-stu-id="fd6f5-110">The following window appears.</span></span>  
  
     ![](../core/media/psadapter-49-ps-configsecurity3.gif "PSAdapter_49_PS_ConfigSecurity3")  
  
5.  <span data-ttu-id="fd6f5-111">按一下向右箭號旁**sign-on Times**索引標籤，顯示多個索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fd6f5-111">Click the right arrow next to the **Sign-on Times** tab to display more tabs.</span></span>  
  
     ![](../core/media/psadapter-50-ps-configsecurity4.gif "PSAdapter_50_PS_ConfigSecurity4")  
  
6.  <span data-ttu-id="fd6f5-112">按一下**元件介面** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fd6f5-112">Click the **Component Interfaces** tab.</span></span>  
  
7.  <span data-ttu-id="fd6f5-113">按一下 + （加號） 新增至新的資料列**元件介面**清單。</span><span class="sxs-lookup"><span data-stu-id="fd6f5-113">Click the + (plus) sign to add a new row to the **Component Interfaces** list.</span></span>  
  
     <span data-ttu-id="fd6f5-114">此時就會顯示您可以在其中輸入元件介面名稱的欄位。</span><span class="sxs-lookup"><span data-stu-id="fd6f5-114">A field appears in which you can type the component interface name.</span></span>  
  
     ![](../core/media/psadapter-51-ps-configsecurity5.gif "PSAdapter_51_PS_ConfigSecurity5")  
  
8.  <span data-ttu-id="fd6f5-115">輸入元件介面名稱，然後按一下**編輯**。</span><span class="sxs-lookup"><span data-stu-id="fd6f5-115">Type the component interface name, and then click **Edit**.</span></span>  
  
     <span data-ttu-id="fd6f5-116">這則範例會使用元件介面 AR_ITEM_AGENT。</span><span class="sxs-lookup"><span data-stu-id="fd6f5-116">This example uses component interface AR_ITEM_AGENT.</span></span>  
  
     ![](../core/media/psadapter-52-ps-configsecurity6.gif "PSAdapter_52_PS_ConfigSecurity6")  
  
9. <span data-ttu-id="fd6f5-117">在清單中，選取所需的存取層級，每個方法，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="fd6f5-117">In the list, select the desired access level for each method, and then click **OK**.</span></span>  
  
     <span data-ttu-id="fd6f5-118">此時就會顯示下列視窗。</span><span class="sxs-lookup"><span data-stu-id="fd6f5-118">The following window appears.</span></span>  
  
     ![](../core/media/psadapter-53-ps-configsecurity7.gif "PSAdapter_53_PS_ConfigSecurity7")  
  
10. <span data-ttu-id="fd6f5-119">在右窗格中，向下捲動，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="fd6f5-119">Scroll down in the right pane, and click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd6f5-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd6f5-120">See Also</span></span>  
 <span data-ttu-id="fd6f5-121">[附錄 a： 元件介面方法](../core/appendix-a-component-interface-methods.md) </span><span class="sxs-lookup"><span data-stu-id="fd6f5-121">[Appendix A: Component Interface Methods](../core/appendix-a-component-interface-methods.md) </span></span>  
 [<span data-ttu-id="fd6f5-122">附錄 c： 使用元件介面</span><span class="sxs-lookup"><span data-stu-id="fd6f5-122">Appendix C: Using Component Interfaces</span></span>](../core/appendix-c-using-component-interfaces.md)