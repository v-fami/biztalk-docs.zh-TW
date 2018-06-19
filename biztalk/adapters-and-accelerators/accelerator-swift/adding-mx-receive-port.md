---
title: 新增 MX 接收埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4818d6af-df1d-481e-becf-1af633735248
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69123b876bdda4b5f999277a1710cdeb1cb61fe7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209478"
---
# <a name="adding-mx-receive-port"></a><span data-ttu-id="fe1e1-102">新增 MX 接收埠</span><span class="sxs-lookup"><span data-stu-id="fe1e1-102">Adding MX Receive Port</span></span>
<span data-ttu-id="fe1e1-103">**新增 MX 接收埠：**</span><span class="sxs-lookup"><span data-stu-id="fe1e1-103">**To add an MX receive port:**</span></span>  
  
1.  <span data-ttu-id="fe1e1-104">啟動**BizTalk Server 管理**主控台。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-104">Start **BizTalk Server Administration** console.</span></span>  
  
2.  <span data-ttu-id="fe1e1-105">在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開  **BizTalk Application 1**。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-105">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
3.  <span data-ttu-id="fe1e1-106">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-106">Right-click **Receive Ports**, point to **New**, and then click **One-Way Receive Port**.</span></span>  
  
4.  <span data-ttu-id="fe1e1-107">在 [接收埠屬性] 對話方塊的 [名稱] 方塊中輸入**MX_ 接收埠**。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-107">In the Receive Port Properties dialog box, in the Name box, type **MX_ Receive Port**.</span></span>  
  
5.  <span data-ttu-id="fe1e1-108">按一下**套用**來繫結連接埠，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-108">Click **Apply** to bind the port, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="fe1e1-109">以滑鼠右鍵按一下**接收位置**，指向 **新增**，然後按一下 **單向接收位置**。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-109">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
7.  <span data-ttu-id="fe1e1-110">在 選取接收埠 對話方塊中，按一下  **MX_ 接收埠**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-110">In the Select a Receive Port dialog box, click **MX_ Receive Port**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="fe1e1-111">在 [接收位置屬性] 對話方塊的 [名稱] 方塊中輸入**MX_ 接收位置**。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-111">In the Receive Location Properties dialog box, in the Name box, type **MX_ Receive Location**.</span></span>  
  
9. <span data-ttu-id="fe1e1-112">在 [傳輸] 區段中，類型的文字方塊中，按一下下拉式清單，然後**檔案**。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-112">In the Transport section, for the Type text box, click the drop-down list, and then select **FILE**.</span></span>  
  
10. <span data-ttu-id="fe1e1-113">按一下**設定**按鈕右邊的 [類型] 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-113">Click the **Configure** button to the right of the Type drop-down list.</span></span>  
  
11. <span data-ttu-id="fe1e1-114">在 FILE 傳輸屬性 對話方塊中，按一下**瀏覽**，然後選取 檔案位置。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-114">In the FILE Transport Properties dialog box, click **Browse**, and then select a file location.</span></span>  
  
12. <span data-ttu-id="fe1e1-115">在 [FILE 傳輸屬性] 對話方塊中，確定\*.xml 檔案遮罩] 方塊中，輸入，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-115">In the FILE Transport Properties dialog box, ensure that \*.xml is entered in the File Mask box, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="fe1e1-116">在 [接收位置屬性] 對話方塊中，確認 [biztalkserverapplication]，輸入接收處理常式方塊。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-116">In the Receive Location Properties dialog box, ensure that BizTalkServerApplication is entered for the Receive handler box.</span></span>  
  
14. <span data-ttu-id="fe1e1-117">在接收管線] 方塊中，選取**接收管線**（已部署管線專案中的接收管線） 從下拉式清單中，按一下**套用**，然後按一下 [**確定**.</span><span class="sxs-lookup"><span data-stu-id="fe1e1-117">In the Receive Pipeline box, select **Receive Pipeline** (the receive pipeline that has been deployed in the Pipeline project) from the drop-down list, click **Apply**, and then click **OK**.</span></span>  
  
15. <span data-ttu-id="fe1e1-118">以滑鼠右鍵按一下您剛才設定，然後再按一下位置**啟用**。</span><span class="sxs-lookup"><span data-stu-id="fe1e1-118">Right-click the location you have just configured, and then click **Enable**.</span></span>