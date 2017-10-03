---
title: "步驟 1： 指派強式名稱給 Contoso 組件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private process tutorial, assigning strong-names
- strong-named assemblies
ms.assetid: c8ec4593-5a4d-47ab-8799-7b2cd3d15ffc
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7124561b9f842a7cc980c7a54230cd122ae32856
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-assigning-a-strong-name-to-the-contoso-assembly"></a><span data-ttu-id="685a5-102">步驟 1： 指派強式名稱給 Contoso 組件</span><span class="sxs-lookup"><span data-stu-id="685a5-102">Step 1: Assigning a Strong Name to the Contoso Assembly</span></span>
<span data-ttu-id="685a5-103">在此步驟中，您將建立強式名稱並指派給 BizTalk 組件。</span><span class="sxs-lookup"><span data-stu-id="685a5-103">In this step, you create and assign a strong name for your BizTalk assembly.</span></span> <span data-ttu-id="685a5-104">強式名稱藉由指派數位簽章和唯一的金鑰組，保證組件的唯一性。</span><span class="sxs-lookup"><span data-stu-id="685a5-104">A strong name guarantees the uniqueness of an assembly by assigning a digital signature and a unique key pair.</span></span> <span data-ttu-id="685a5-105">此外，強式名稱提供完整性檢查，可保證組件的內容自上次建置以來未曾變更過。</span><span class="sxs-lookup"><span data-stu-id="685a5-105">Additionally, a strong name provides an integrity check to guarantee that the content of the assembly has not changed since you last built it.</span></span>  
  
### <a name="to-create-a-strong-name-assembly-key-file"></a><span data-ttu-id="685a5-106">建立強式名稱組件金鑰檔</span><span class="sxs-lookup"><span data-stu-id="685a5-106">To create a strong name assembly key file</span></span>  
  
1.  <span data-ttu-id="685a5-107">啟動**Visual Studio 2012 的命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="685a5-107">Start **Visual Studio 2012 Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="685a5-108">在命令提示字元下，移至 Contoso 解決方案所在的位置。</span><span class="sxs-lookup"><span data-stu-id="685a5-108">At the command prompt, move to the location of the Contoso solution.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="685a5-109">根據預設，Contoso 解決方案的位置是*\<磁碟機 >*: \Documents and 設定\\*\<使用者名稱 >*documents\visual Studio \<版本 > \Projects。</span><span class="sxs-lookup"><span data-stu-id="685a5-109">By default, the location of the Contoso solution is *\<drive>*:\Documents and Settings\\*\<user name>*\My Documents\Visual Studio \<version>\Projects.</span></span>  
  
3.  <span data-ttu-id="685a5-110">在命令提示字元中，輸入**sn-k FabConPriceAvail.snk**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="685a5-110">At the command prompt, type **sn -k FabConPriceAvail.snk**, and then press **Enter**.</span></span>  
  
4.  <span data-ttu-id="685a5-111">在命令提示字元中，輸入**結束**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="685a5-111">At the command prompt, type **Exit**, and then press **Enter**.</span></span>  
  
### <a name="to-assign-a-strong-name-to-your-assembly"></a><span data-ttu-id="685a5-112">指派強式名稱給組件</span><span class="sxs-lookup"><span data-stu-id="685a5-112">To assign a strong name to your assembly</span></span>  
  
1.  <span data-ttu-id="685a5-113">在 [方案總管] 中，以滑鼠右鍵按一下**ContosoPriceAndAvailability**專案，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="685a5-113">In Solution Explorer, right-click the **ContosoPriceAndAvailability** project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="685a5-114">在 屬性頁中，按一下 **簽署**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="685a5-114">In the Property Pages, click **Signing** in the left pane.</span></span>  
  
3.  <span data-ttu-id="685a5-115">在右窗格中，選取**簽署組件**。</span><span class="sxs-lookup"><span data-stu-id="685a5-115">In the right pane, select **Sign the assembly**.</span></span>  
  
4.  <span data-ttu-id="685a5-116">按一下**瀏覽**在 [選擇強式名稱金鑰檔] 欄位。</span><span class="sxs-lookup"><span data-stu-id="685a5-116">Click **Browse** in the Choose the strong name key file field.</span></span>  
  
5.  <span data-ttu-id="685a5-117">找出您的專案資料夾中，選取**FabConPriceAvail.snk**您稍早建立的檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="685a5-117">Locate your project folder, select the **FabConPriceAvail.snk** file you created earlier, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="685a5-118">按一下**確定**儲存的變更。</span><span class="sxs-lookup"><span data-stu-id="685a5-118">Click **OK** to save the changes.</span></span>  
  
7.  <span data-ttu-id="685a5-119">在 [方案總管] 中，以滑鼠右鍵按一下**ContosoPriceAndAvailability**專案，然後再按一下**建置**。</span><span class="sxs-lookup"><span data-stu-id="685a5-119">In Solution Explorer, right-click the **ContosoPriceAndAvailability** project, and then click **Build**.</span></span> <span data-ttu-id="685a5-120">建置成功之後，以滑鼠右鍵按一下專案，然後**部署**。</span><span class="sxs-lookup"><span data-stu-id="685a5-120">After the build has succeeded, right-click the project again, and then click **Deploy**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="685a5-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="685a5-121">See Also</span></span>  
 [<span data-ttu-id="685a5-122">步驟 2： 為 Contoso 3A2 價格與可用性查詢/回應實例建立連接埠</span><span class="sxs-lookup"><span data-stu-id="685a5-122">Step 2: Creating Ports for the Contoso 3A2 Price and Availability Query/Response Scenario</span></span>](step-2-create-ports-for-contoso-3a2-price-and-availability-query.md)