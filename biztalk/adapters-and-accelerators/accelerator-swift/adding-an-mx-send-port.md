---
title: 新增 MX 傳送埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3ad5d2f-1fcb-49d4-9974-664733308f45
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3cd4c16658ad0ff6b85976fbc6a97c4f397acbdb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22208910"
---
# <a name="adding-an-mx-send-port"></a><span data-ttu-id="fd404-102">新增 MX 傳送連接埠</span><span class="sxs-lookup"><span data-stu-id="fd404-102">Adding an MX Send Port</span></span>
<span data-ttu-id="fd404-103">**若要新增 MX 傳送埠：**</span><span class="sxs-lookup"><span data-stu-id="fd404-103">**To add an MX send port:**</span></span>  
  
1.  <span data-ttu-id="fd404-104">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="fd404-104">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-Way Send Port**.</span></span>  
  
2.  <span data-ttu-id="fd404-105">在 傳送埠屬性 對話方塊中，在 名稱方塊中，輸入**MX_SendPort**。</span><span class="sxs-lookup"><span data-stu-id="fd404-105">In the Send Port Properties dialog box, in the Name box type **MX_SendPort**.</span></span>  
  
3.  <span data-ttu-id="fd404-106">在 [傳輸] 區段的 [類型] 方塊中，按一下下拉式清單，然後**檔案**。</span><span class="sxs-lookup"><span data-stu-id="fd404-106">In the Transport section, for the Type box, click the drop-down list, and then select **FILE**.</span></span>  
  
4.  <span data-ttu-id="fd404-107">按一下**設定**按鈕右邊的 [類型] 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="fd404-107">Click the **Configure** button to the right of the Type drop-down list.</span></span>  
  
5.  <span data-ttu-id="fd404-108">在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="fd404-108">In the FILE Transport Properties dialog box, click **Browse**.</span></span>  
  
6.  <span data-ttu-id="fd404-109">在瀏覽資料夾] 對話方塊中，選取 [檔案位置。</span><span class="sxs-lookup"><span data-stu-id="fd404-109">In the Browse for Folder dialog box, select a file location.</span></span>  
  
7.  <span data-ttu-id="fd404-110">在 檔案名稱 方塊中，輸入 **%MessageID%.xml**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="fd404-110">In the File name box, type **%MessageID%.xml**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="fd404-111">在 [傳送埠屬性] 對話方塊中，按一下 [傳送管線] 方塊中的下拉式清單，然後選取傳送管線已部署管線專案中。</span><span class="sxs-lookup"><span data-stu-id="fd404-111">In the Send Port Properties dialog box, click the drop-down list for the send pipeline box, and then select the send pipeline you have deployed in the pipeline project.</span></span>  
  
9. <span data-ttu-id="fd404-112">在左窗格中，按一下 **篩選**，然後指定下列：</span><span class="sxs-lookup"><span data-stu-id="fd404-112">In the left pane, click **Filters**, and then specify the following:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="fd404-113">屬性</span><span class="sxs-lookup"><span data-stu-id="fd404-113">Property</span></span>|<span data-ttu-id="fd404-114">Microsoft.Solutions.MX_A4SWIFT。Property.MX_A4SWIFT_Failed</span><span class="sxs-lookup"><span data-stu-id="fd404-114">Microsoft.Solutions.MX_A4SWIFT.Property.MX_A4SWIFT_Failed</span></span>|  
    |<span data-ttu-id="fd404-115">運算子</span><span class="sxs-lookup"><span data-stu-id="fd404-115">Operator</span></span>|<span data-ttu-id="fd404-116">選取 = =</span><span class="sxs-lookup"><span data-stu-id="fd404-116">Select ==</span></span>|  
    |<span data-ttu-id="fd404-117">值</span><span class="sxs-lookup"><span data-stu-id="fd404-117">Value</span></span>|<span data-ttu-id="fd404-118">False</span><span class="sxs-lookup"><span data-stu-id="fd404-118">False</span></span>|  
  
10. <span data-ttu-id="fd404-119">按一下**套用**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="fd404-119">Click **Apply**, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="fd404-120">在 傳送埠 窗格中，以滑鼠右鍵按一下**MX_SendPort**，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="fd404-120">In the Send Ports pane, right-click **MX_SendPort**, and then click **Start**.</span></span>