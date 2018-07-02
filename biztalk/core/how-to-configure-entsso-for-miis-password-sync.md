---
title: 如何設定 ENTSSO 以進行 MIIS 密碼同步 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 89438935-37c1-4ac9-9ca2-7af8d9bfd3ae
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9aed37b5b3883242005f46dcc6a0253a4971d680
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005223"
---
# <a name="how-to-configure-entsso-for-miis-password-sync"></a><span data-ttu-id="a1f66-102">如何設定 ENTSSO 以進行 MIIS 密碼同步</span><span class="sxs-lookup"><span data-stu-id="a1f66-102">How to Configure ENTSSO for MIIS Password Sync</span></span>
<span data-ttu-id="a1f66-103">在設定 XML 檔案和 Microsoft Identity Integration Server (MIIS) 之後，剩下的組態步驟是在企業單一登入 (ENTSSO) 系統中執行。</span><span class="sxs-lookup"><span data-stu-id="a1f66-103">After configuring the XML file and Microsoft Identity Integration Server (MIIS), the remaining configuration steps take place in the Enterprise Single Sign-On (ENTSSO) system.</span></span>  
  
### <a name="to-allow-password-sync-from-miis"></a><span data-ttu-id="a1f66-104">若要允許從 MIIS 進行密碼同步</span><span class="sxs-lookup"><span data-stu-id="a1f66-104">To allow Password Sync from MIIS</span></span>  
  
1.  <span data-ttu-id="a1f66-105">在 企業單一登入，請按一下**伺服器**節點。</span><span class="sxs-lookup"><span data-stu-id="a1f66-105">In Enterprise Single Sign-On, click the **Servers** node.</span></span>  
  
2.  <span data-ttu-id="a1f66-106">以滑鼠右鍵按一下適當的伺服器，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="a1f66-106">Right-click the appropriate server, and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="a1f66-107">按一下 [**密碼同步處理**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a1f66-107">Click the **Password Sync** tab.</span></span>  
  
4.  <span data-ttu-id="a1f66-108">選取 **允許從 MIIS 進行密碼同步處理**。</span><span class="sxs-lookup"><span data-stu-id="a1f66-108">Select **Allow password sync from MIIS**.</span></span>  
  
5.  <span data-ttu-id="a1f66-109">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="a1f66-109">Click **OK**.</span></span>  
  
### <a name="to-enable-password-sync-on-the-system-level"></a><span data-ttu-id="a1f66-110">若要啟用系統層級的密碼同步</span><span class="sxs-lookup"><span data-stu-id="a1f66-110">To enable Password Sync on the system level</span></span>  
  
1. <span data-ttu-id="a1f66-111">在 企業單一登入，請以滑鼠右鍵按一下**系統**節點。</span><span class="sxs-lookup"><span data-stu-id="a1f66-111">In Enterprise Single Sign-On, right-click the **System** node.</span></span>  
  
2. <span data-ttu-id="a1f66-112">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="a1f66-112">Click **Properties**.</span></span>  
  
    <span data-ttu-id="a1f66-113">**屬性** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="a1f66-113">The **Properties** dialog box appears.</span></span>  
  
3. <span data-ttu-id="a1f66-114">按一下 [**選項**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a1f66-114">Click the **Options** tab.</span></span>  
  
4. <span data-ttu-id="a1f66-115">在 **啟用密碼同步處理**欄位中，選取**從 Windows 到配接器**。</span><span class="sxs-lookup"><span data-stu-id="a1f66-115">In the **Enable Password Sync** field, select **From Windows to Adapters**.</span></span>  
  
    <span data-ttu-id="a1f66-116">**其他設定**</span><span class="sxs-lookup"><span data-stu-id="a1f66-116">**Additional Configuration**</span></span>  
  
    <span data-ttu-id="a1f66-117">最後，您必須設定下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="a1f66-117">Finally, you must configure one of the following:</span></span>  
  
   - <span data-ttu-id="a1f66-118">接受 Windows 密碼同步的密碼同步配接器。</span><span class="sxs-lookup"><span data-stu-id="a1f66-118">A Password Sync Adapter that accepts Windows Password Sync.</span></span>  
  
   - <span data-ttu-id="a1f66-119">至少在一個應用程式上啟用的直接密碼同步。</span><span class="sxs-lookup"><span data-stu-id="a1f66-119">Direct Password Sync enabled on at least one application.</span></span>  
  
     <span data-ttu-id="a1f66-120">如需如何進行這項設定的詳細資訊，請參閱密碼同步相關文件。</span><span class="sxs-lookup"><span data-stu-id="a1f66-120">For information about how to do this, refer to your Password Sync documentation.</span></span>  
  
### <a name="to-configure-the-entsso-ma-for-miis-password-sync"></a><span data-ttu-id="a1f66-121">若要設定 EntSSO MA 以進行 MIIS 密碼同步</span><span class="sxs-lookup"><span data-stu-id="a1f66-121">To configure the EntSSO MA for MIIS Password Sync</span></span>  
  
1.  <span data-ttu-id="a1f66-122">在 ENTSSO 管理代理程式**屬性**頁面上，按一下**Configure Extensions**。</span><span class="sxs-lookup"><span data-stu-id="a1f66-122">On the ENTSSO Management Agent **Properties** page, click **Configure Extensions**.</span></span>  
  
2.  <span data-ttu-id="a1f66-123">在 **密碼延伸模組的連接資訊**欄位中，按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="a1f66-123">In the **Connection information for password extension** field, click **Settings**.</span></span>  
  
3.  <span data-ttu-id="a1f66-124">在 **連接到**欄位中，輸入將接收密碼變更電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="a1f66-124">In the **Connect To** field enter the name of the computer that will receive the password changes.</span></span>  
  
     <span data-ttu-id="a1f66-125">電腦名稱的格式必須與在網域中為 ENTSSO 服務建立服務主要名稱 (SPN) 時使用的格式相同。</span><span class="sxs-lookup"><span data-stu-id="a1f66-125">The computer name must be in the same format that was used when creating the Service Principal Name (SPN) for the ENTSSO service on the domain.</span></span>  
  
     <span data-ttu-id="a1f66-126">例如：</span><span class="sxs-lookup"><span data-stu-id="a1f66-126">For example:</span></span>  
  
     <span data-ttu-id="a1f66-127">若簡短格式為 SPN = ENTSSO/ABCD1411，則輸入 ABCD1411</span><span class="sxs-lookup"><span data-stu-id="a1f66-127">Short format - SPN = ENTSSO/ABCD1411, then enter ABCD1411</span></span>  
  
4.  <span data-ttu-id="a1f66-128">若長格式為 SPN = ENTSSO/ABCD1411.CompanyName.com，則輸入 ABCD1411.CompanyName.com</span><span class="sxs-lookup"><span data-stu-id="a1f66-128">Long format - SPN = ENTSSO/ABCD1411.CompanyName.com then enter ABCD1411.CompanyName.com</span></span>  
  
### <a name="additional-configuration-steps"></a><span data-ttu-id="a1f66-129">其他組態步驟</span><span class="sxs-lookup"><span data-stu-id="a1f66-129">Additional Configuration Steps</span></span>  
  
1.  <span data-ttu-id="a1f66-130">按一下 **開始**，指向**所有程式**，指向**Microsoft Identity Integration Server**，然後按一下**Identity Manager**。</span><span class="sxs-lookup"><span data-stu-id="a1f66-130">Click **Start**, point to **All Programs**, point to **Microsoft Identity Integration Server**, and then click **Identity Manager**.</span></span>  
  
2.  <span data-ttu-id="a1f66-131">在 **[工具]** 功能表上，按一下 **[選項]**。</span><span class="sxs-lookup"><span data-stu-id="a1f66-131">On the **Tools** menu, click **Options**.</span></span>  
  
3.  <span data-ttu-id="a1f66-132">選取 **啟用密碼同步處理**。</span><span class="sxs-lookup"><span data-stu-id="a1f66-132">Select **Enable Password Synchronization**.</span></span>  
  
4.  <span data-ttu-id="a1f66-133">在 **管理代理程式檢視**，選取**ADMA**。</span><span class="sxs-lookup"><span data-stu-id="a1f66-133">In the **Management Agents view**, select **ADMA**.</span></span>  
  
5.  <span data-ttu-id="a1f66-134">在 **動作**窗格中，選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="a1f66-134">In the **Action** pane, select **Properties**.</span></span>  
  
6.  <span data-ttu-id="a1f66-135">在 **屬性**頁面上，選取**設定目錄分割**，然後選取**啟用此磁碟分割做為密碼同步處理來源**。</span><span class="sxs-lookup"><span data-stu-id="a1f66-135">On the **Properties** page, select **Configure Directory Partitions**, and then select **Enable this partition as a password synchronization source**.</span></span>  
  
7.  <span data-ttu-id="a1f66-136">按一下 **目標**，然後選取 entssoma2，讓它能夠從 MIIS 接收密碼變更。</span><span class="sxs-lookup"><span data-stu-id="a1f66-136">Click **Targets**, and then select ENTSSOMA2 to enable it to receive password changes from MIIS.</span></span> <span data-ttu-id="a1f66-137">取消選取 ENTSSOMA。</span><span class="sxs-lookup"><span data-stu-id="a1f66-137">Deselect ENTSSOMA.</span></span> <span data-ttu-id="a1f66-138">按一下  **確定**，然後按一下**確定**一次。</span><span class="sxs-lookup"><span data-stu-id="a1f66-138">Click **OK**, and then click **OK** again.</span></span>  
  
8.  <span data-ttu-id="a1f66-139">在 **管理代理程式**檢視中，選取**entssoma2**。</span><span class="sxs-lookup"><span data-stu-id="a1f66-139">In the **Management Agent** view, select **ENTSSOMA2**.</span></span> <span data-ttu-id="a1f66-140">在右窗格中，選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="a1f66-140">In the right-hand pane, select **Properties**.</span></span> <span data-ttu-id="a1f66-141">在上**屬性**頁面上，按一下**Configure Extensions**。</span><span class="sxs-lookup"><span data-stu-id="a1f66-141">On the **Properties** page, click **Configure Extensions**.</span></span>  
  
9. <span data-ttu-id="a1f66-142">確認**啟用密碼管理**已選取，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="a1f66-142">Confirm that **Enable password management** is selected, and then click **Settings**.</span></span>  
  
10. <span data-ttu-id="a1f66-143">在 [**連線設定**] 對話方塊中，指定下列項目：</span><span class="sxs-lookup"><span data-stu-id="a1f66-143">In the **Connection Settings** dialog, specify the following:</span></span>  
  
    -   <span data-ttu-id="a1f66-144">連接到： INTSVR1.fabrikam.com</span><span class="sxs-lookup"><span data-stu-id="a1f66-144">Connect To: INTSVR1.fabrikam.com</span></span>  
  
    -   <span data-ttu-id="a1f66-145">使用者： fabrikam\ssosvcact</span><span class="sxs-lookup"><span data-stu-id="a1f66-145">User: fabrikam\ssosvcact</span></span>  
  
    -   <span data-ttu-id="a1f66-146">密碼： ssosvcact</span><span class="sxs-lookup"><span data-stu-id="a1f66-146">Password: ssosvcact</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="a1f66-147">這個帳戶應該符合 INTSVR1.fabrikam.com 上設定的 ENTSSO 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="a1f66-147">This account should match the ENTSSO service account configured on INTSVR1.fabrikam.com.</span></span>  
  
11. <span data-ttu-id="a1f66-148">按一下  **確定**，然後按一下**確定**一次。</span><span class="sxs-lookup"><span data-stu-id="a1f66-148">Click **OK**, and then click **OK** again.</span></span>  
  
12. <span data-ttu-id="a1f66-149">您也可以停用 MIIS 的密碼同步。</span><span class="sxs-lookup"><span data-stu-id="a1f66-149">You can also disable password sync for MIIS.</span></span> <span data-ttu-id="a1f66-150">若要這樣做，請在**Identity Manager**，按一下**工具**功能表上，按一下 **選項**，然後取消選取**Enable Password Synchronization**。</span><span class="sxs-lookup"><span data-stu-id="a1f66-150">To do this, in **Identity Manager**, click the **Tools** menu, click **Options**, and then deselect **Enable Password Synchronization**.</span></span>  
  
     <span data-ttu-id="a1f66-151">適用的限制如下：</span><span class="sxs-lookup"><span data-stu-id="a1f66-151">The following restrictions will apply:</span></span>  
  
    -   <span data-ttu-id="a1f66-152">您必須在與 ENTSSO 管理代理程式通訊的 ENTSSO 服務帳戶上設定 SPN，密碼同步才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="a1f66-152">For Password Sync to function properly, SPN must be configured on the ENTSSO service account that the ENTSSO Management Agent will communicate with.</span></span>  
  
    -   <span data-ttu-id="a1f66-153">MIIS 和 ENTSSO 服務之間的通訊需要 Kerberos。</span><span class="sxs-lookup"><span data-stu-id="a1f66-153">Communication between MIIS and the ENTSSO server requires Kerberos.</span></span>  
  
13. <span data-ttu-id="a1f66-154">在 ENTSSO 管理代理程式的 MIIS 連線組態中設定密碼延伸模組時，指定的帳戶必須符合從 MIIS 接收密碼之 ENTSSO 伺服器的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="a1f66-154">When configuring Password Extension in the MIIS connection configuration for the ENTSSO Management Agent, the account specified must match the service account for the ENTSSO server that will receive passwords from MIIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1f66-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1f66-155">See Also</span></span>  
 [<span data-ttu-id="a1f66-156">如何使用 ENTSSO 管理代理程式</span><span class="sxs-lookup"><span data-stu-id="a1f66-156">How to Use the ENTSSO Management Agent</span></span>](../core/how-to-use-the-entsso-management-agent.md)