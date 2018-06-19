---
title: 錯誤-運算質固定輸入不相符 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.functoidFixedInputMismatch
ms.assetid: d235e7c3-efcf-4128-aef7-cdfdf1f317be
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8de4020105f357905e510be1694c0cf95a4af6c2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968348"
---
# <a name="error---functoid-fixed-input-mismatch"></a><span data-ttu-id="b2310-102">錯誤-運算質固定輸入不相符</span><span class="sxs-lookup"><span data-stu-id="b2310-102">Error - Functoid Fixed Input Mismatch</span></span>
<span data-ttu-id="b2310-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="b2310-103">**Error Code**</span></span>  
  
 <span data-ttu-id="b2310-104">btm1010</span><span class="sxs-lookup"><span data-stu-id="b2310-104">btm1010</span></span>  
  
 <span data-ttu-id="b2310-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="b2310-105">**Explanation**</span></span>  
  
 <span data-ttu-id="b2310-106">指出的運算質未指定正確的輸入參數數目。</span><span class="sxs-lookup"><span data-stu-id="b2310-106">The indicated functoid does not have the correct number of input parameters specified.</span></span> <span data-ttu-id="b2310-107">輸入參數的數目必須與指定的相同。</span><span class="sxs-lookup"><span data-stu-id="b2310-107">The number of input parameters must be exactly as specified.</span></span>  
  
 <span data-ttu-id="b2310-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="b2310-108">**User Action**</span></span>  
  
 <span data-ttu-id="b2310-109">使用下列一或多種方式，針對指定的運算質提供指定數目的輸入參數，應特別注意輸入參數的順序：</span><span class="sxs-lookup"><span data-stu-id="b2310-109">Use one or more of the following methods to provide the indicated number of input parameters to the indicated functoid, paying particular attention to the expected order of input parameters:</span></span>  
  
-   <span data-ttu-id="b2310-110">若要建立其他連結，請使用拖曳方式在指定的運算質與來源結構描述中之節點或其他運算質之輸出間建立連結，這些節點位於指定運算質左邊的地圖格線頁中。</span><span class="sxs-lookup"><span data-stu-id="b2310-110">To create additional links, drag to create links between the indicated functoid and either nodes in the source schema or the output of other functoids that are located to the left of the indicated functoid in a map grid page.</span></span>  
  
-   <span data-ttu-id="b2310-111">若要建立其他連結，請選取指定的運算質，按一下省略符號 (**...**) 相關聯的按鈕**輸入參數**屬性[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗中，然後設定並重新安排輸入參數順序**設定\<運算質\>運算質** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b2310-111">To create additional links, select the indicated functoid, click the ellipsis (**...**) button associated with the **Input Parameters** property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then configure and rearrange the order of the input parameters in the **Configure \<Functoid\> Functoid** dialog box.</span></span> <span data-ttu-id="b2310-112">您可以在此對話方塊中建立常數輸入參數、賦予這些參數值，並使用相對於其他輸入參數的順序排列這些參數。</span><span class="sxs-lookup"><span data-stu-id="b2310-112">Constant input parameters can be created, given values, and put in the proper order relative to the other input parameters in this dialog box.</span></span>  
  
-   <span data-ttu-id="b2310-113">若要移除現有連結，為每個連線到指定的運算質左側的連結連結上按一下滑鼠右鍵，然後按一下 **刪除**。</span><span class="sxs-lookup"><span data-stu-id="b2310-113">To remove existing links, for each link connected to the left side of the indicated functoid, right-click the link and then click **Delete**.</span></span>  
  
-   <span data-ttu-id="b2310-114">若要移除現有連結，選取指定的運算質，請按一下省略符號 (**...**) 相關聯的按鈕**輸入參數**屬性[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗中，然後在**設定\<運算質\>運算質**對話方塊中，刪除所有輸入參數選取並按一下![ ] (../core/media/bts-tls-paramdelete.gif "bts_tls_paramdelete")為每個按鈕。</span><span class="sxs-lookup"><span data-stu-id="b2310-114">To remove existing links, select the indicated functoid, click the ellipsis (**...**) button associated with the **Input Parameters** property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then in the **Configure \<Functoid\> Functoid** dialog box, delete all input parameters by selecting and clicking the ![](../core/media/bts-tls-paramdelete.gif "bts_tls_paramdelete") button for each of them.</span></span> <span data-ttu-id="b2310-115">您必須使用此方式來刪除常數輸入參數。</span><span class="sxs-lookup"><span data-stu-id="b2310-115">You must use this method to delete constant input parameters.</span></span>