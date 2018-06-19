---
title: 如何設定 ENTSSO MA 的 MIIS |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c7820384-ff64-4628-9e35-02b13803928f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 969a52beb02c3d2ba237369c16efec9ee84e2ef1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248134"
---
# <a name="how-to-configure-miis-for-entsso-ma"></a><span data-ttu-id="c7411-102">如何設定 ENTSSO MA 的 MIIS</span><span class="sxs-lookup"><span data-stu-id="c7411-102">How to Configure MIIS for ENTSSO MA</span></span>
<span data-ttu-id="c7411-103">當您在執行 Microsoft Identity Integration Server (MIIS) 的電腦上安裝企業單一登入 (SSO) 管理功能 (完整版本或僅限管理版本) 時，ENTSSO 管理代理程式也會自動安裝 。</span><span class="sxs-lookup"><span data-stu-id="c7411-103">When you install the Enterprise Single Sign-On (SSO) Administration feature (either the full version or the Admin-only version) on a computer running Microsoft Identity Integration Server (MIIS), the ENTSSO Management Agent is automatically installed.</span></span> <span data-ttu-id="c7411-104">這表示當您開啟 MIIS 時，幾乎所有組態都已經設定完成。</span><span class="sxs-lookup"><span data-stu-id="c7411-104">This means that when you open MIIS, nearly all of the configuration has already been done.</span></span> <span data-ttu-id="c7411-105">唯一缺少的部分是連線資訊。</span><span class="sxs-lookup"><span data-stu-id="c7411-105">The only part missing is the connection information.</span></span>  
  
 <span data-ttu-id="c7411-106">開始此程序之前，請先確定備妥下列資訊：</span><span class="sxs-lookup"><span data-stu-id="c7411-106">Before starting this procedure, make sure you have the following information available:</span></span>  
  
-   <span data-ttu-id="c7411-107">ENTSSO 伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="c7411-107">ENTSSO Server name.</span></span>  
  
-   <span data-ttu-id="c7411-108">ENTSSO 管理代理程式用來與 SSO 伺服器通訊的 Windows 帳戶使用者識別碼和密碼。</span><span class="sxs-lookup"><span data-stu-id="c7411-108">UserId and password of the Windows account under which the ENTSSO Management Agent will communicate with the SSO Server.</span></span>  
  
### <a name="to-configure-the-management-agent-within-miis"></a><span data-ttu-id="c7411-109">若要在 MIIS 中設定管理代理程式</span><span class="sxs-lookup"><span data-stu-id="c7411-109">To configure the Management Agent within MIIS</span></span>  
  
1.  <span data-ttu-id="c7411-110">開啟 MIIS，然後開啟**Identity Manager**。</span><span class="sxs-lookup"><span data-stu-id="c7411-110">Open MIIS, and open the **Identity Manager**.</span></span>  
  
2.  <span data-ttu-id="c7411-111">開啟**建立管理代理程式** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c7411-111">Open the **Create Management Agent** dialog box.</span></span>  
  
3.  <span data-ttu-id="c7411-112">選取**企業單一登入**清單中。</span><span class="sxs-lookup"><span data-stu-id="c7411-112">Select **Enterprise Single Sign-On** in the list.</span></span>  
  
     <span data-ttu-id="c7411-113">這會啟動**建立管理代理程式精靈**。</span><span class="sxs-lookup"><span data-stu-id="c7411-113">This starts the **Create Management Agent Wizard**.</span></span>  
  
4.  <span data-ttu-id="c7411-114">在**設定連線資訊**頁面上，於**連接到：** 欄位中，輸入 SSO 伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="c7411-114">On the **Configure Connection Information** page, in the **Connect To:** field, enter the name of the SSO Server.</span></span>  
  
5.  <span data-ttu-id="c7411-115">輸入 ENTSSO 管理代理程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="c7411-115">Enter the name of the ENTSSO Management Agent.</span></span> <span data-ttu-id="c7411-116">這個名稱必須與 ENTSSO.xml 檔案中指定的名稱相符。</span><span class="sxs-lookup"><span data-stu-id="c7411-116">This name must match the name specified in your ENTSSO.xml file.</span></span>  
  
6.  <span data-ttu-id="c7411-117">在**使用者**欄位中，指定 ENTSSO 管理代理程式會使用來管理 SSO 資料庫中的對應的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="c7411-117">In the **User** field, specify the domain account that the ENTSSO Management Agent uses to manage mappings in the SSO Database.</span></span>  
  
     <span data-ttu-id="c7411-118">這個帳戶必須是 SSO 系統中 SSO 分支機構系統管理員或 SSO 系統管理員帳戶的成員。</span><span class="sxs-lookup"><span data-stu-id="c7411-118">This account should be either a member of the SSO Affiliate Administrators or SSO Administrators accounts within the SSO System.</span></span>  
  
7.  <span data-ttu-id="c7411-119">在**密碼**欄位中，輸入該使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="c7411-119">In the **Password** field, enter the password for that user.</span></span>  
  
8.  <span data-ttu-id="c7411-120">按一下**下一步**，接受預設值，直到您到達**設定延伸模組**頁面。</span><span class="sxs-lookup"><span data-stu-id="c7411-120">Click **Next**, accepting the defaults until you reach the **Configure Extensions** page.</span></span>  
  
9. <span data-ttu-id="c7411-121">接近**連接資訊**密碼延伸模組中，按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="c7411-121">Near **Connection information** for password extension, click **Settings**.</span></span>  
  
     <span data-ttu-id="c7411-122">**連線設定** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="c7411-122">The **Connection Settings** dialog box appears.</span></span>  
  
10. <span data-ttu-id="c7411-123">在**連接到**方塊中，輸入適當的帳戶。</span><span class="sxs-lookup"><span data-stu-id="c7411-123">In the **Connect To** box, enter the appropriate account.</span></span> <span data-ttu-id="c7411-124">這個帳戶必須與所指定電腦上執行之 ENTSSO 服務的服務帳戶相同。</span><span class="sxs-lookup"><span data-stu-id="c7411-124">This account must be the same as the service account for the ENTSSO service running on the computer specified.</span></span>  
  
11. <span data-ttu-id="c7411-125">在**使用者**和**密碼**欄位中，輸入使用者名稱和密碼的帳戶。</span><span class="sxs-lookup"><span data-stu-id="c7411-125">In the **User** and **Password** fields, enter the user name and password for the account.</span></span>  
  
12. <span data-ttu-id="c7411-126">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="c7411-126">Click **OK**.</span></span>  
  
13. <span data-ttu-id="c7411-127">在**MIISCreate 管理代理程式**，按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="c7411-127">In the **MIISCreate Management Agent**, click **Finish**.</span></span>  
  
14. <span data-ttu-id="c7411-128">在**Identity Manager**，按一下 **工具**功能表，然後再按一下**選項**。</span><span class="sxs-lookup"><span data-stu-id="c7411-128">While still in the **Identity Manager**, click the **Tools** menu, and then click **Options**.</span></span>  
  
     <span data-ttu-id="c7411-129">**選項** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="c7411-129">The **Options** dialog box appears.</span></span>  
  
15. <span data-ttu-id="c7411-130">選取**啟用 metaverse 規則延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="c7411-130">Select **Enable metaverse rules extension**.</span></span>  
  
16. <span data-ttu-id="c7411-131">在**規則延伸模組名稱 欄位**，輸入**Microsoft.EnterpriseSingleSignOn.ManagementAgent.dll**。</span><span class="sxs-lookup"><span data-stu-id="c7411-131">In the **Rules extension name field**, enter **Microsoft.EnterpriseSingleSignOn.ManagementAgent.dll**.</span></span>  
  
17. <span data-ttu-id="c7411-132">按一下**確定**，關閉 MIIS。</span><span class="sxs-lookup"><span data-stu-id="c7411-132">Click **OK** and close MIIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7411-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7411-133">See Also</span></span>  
 [<span data-ttu-id="c7411-134">如何使用 ENTSSO 管理代理程式</span><span class="sxs-lookup"><span data-stu-id="c7411-134">How to Use the ENTSSO Management Agent</span></span>](../core/how-to-use-the-entsso-management-agent.md)