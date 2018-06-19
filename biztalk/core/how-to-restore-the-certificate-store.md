---
title: 如何還原憑證存放區 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c6f7551-d119-4668-9b52-6013f69a0302
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aaeee6b762cf5af15ca7cba34864abd86682d4df
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254694"
---
# <a name="how-to-restore-the-certificate-store"></a><span data-ttu-id="58f75-102">如何還原憑證存放區</span><span class="sxs-lookup"><span data-stu-id="58f75-102">How to Restore the Certificate Store</span></span>
<span data-ttu-id="58f75-103">復原過程[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您必須還原憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="58f75-103">As a part of recovering [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you must restore the certificate store.</span></span> <span data-ttu-id="58f75-104">如果您要復原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Standard Edition 中，您必須使用此程序來還原憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="58f75-104">If you are recovering [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Standard Edition, you must use this procedure to restore the certificate store.</span></span> <span data-ttu-id="58f75-105">您不需要復原所有其他版本時，執行此程序[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]因為復原程序會自動還原您的憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="58f75-105">You do not need to perform this procedure when recovering all other editions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] because the recovery process automatically restores the certificate store for you.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="58f75-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="58f75-106">Prerequisites</span></span>  
 <span data-ttu-id="58f75-107">您必須以「系統管理員」群組成員的身分登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="58f75-107">You must be logged on as a member of the Administrators group to perform this procedure.</span></span>  
  
### <a name="to-restore-the-certificate-store-biztalk-server-standard-edition"></a><span data-ttu-id="58f75-108">若要還原憑證存放區 (BizTalk Server Standard Edition)</span><span class="sxs-lookup"><span data-stu-id="58f75-108">To restore the certificate store (BizTalk Server Standard Edition)</span></span>  
  
1.  <span data-ttu-id="58f75-109">按一下**啟動**，按一下 **所有程式**，然後按一下  **Internet Explorer**。</span><span class="sxs-lookup"><span data-stu-id="58f75-109">Click **Start**, click **All Programs**, and then click **Internet Explorer**.</span></span>  
  
2.  <span data-ttu-id="58f75-110">在**工具**功能表上，按一下 **網際網路選項**。</span><span class="sxs-lookup"><span data-stu-id="58f75-110">On the **Tools** menu, click **Internet Options**.</span></span>  
  
3.  <span data-ttu-id="58f75-111">在**網際網路選項**對話方塊中，按一下 **內容**索引標籤，然後再按一下**憑證**。</span><span class="sxs-lookup"><span data-stu-id="58f75-111">In the **Internet Options** dialog box, click the **Content** tab, and then click **Certificates**.</span></span>  
  
4.  <span data-ttu-id="58f75-112">在**憑證**對話方塊中，按一下 **其他人**索引標籤，然後再按一下**匯入**。</span><span class="sxs-lookup"><span data-stu-id="58f75-112">In the **Certificates** dialog box, click the **Other People** tab, and then click **Import**.</span></span>  
  
5.  <span data-ttu-id="58f75-113">在**憑證匯入精靈**，按一下 **取消**。</span><span class="sxs-lookup"><span data-stu-id="58f75-113">In the **Certificate Import Wizard**, click **Cancel**.</span></span>  
  
     <span data-ttu-id="58f75-114">這會建立**AddressBook**登錄中的登錄區。</span><span class="sxs-lookup"><span data-stu-id="58f75-114">This creates the **AddressBook** hive in the registry.</span></span>  
  
6.  <span data-ttu-id="58f75-115">在**憑證**對話方塊中，按一下 **關閉**。</span><span class="sxs-lookup"><span data-stu-id="58f75-115">In the **Certificates** dialog box, click **Close**.</span></span>  
  
7.  <span data-ttu-id="58f75-116">在**網際網路選項**對話方塊中，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="58f75-116">In the **Internet Options** dialog box, click **OK**.</span></span>  
  
8.  <span data-ttu-id="58f75-117">按一下**檔案**，然後按一下 **關閉**結束 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="58f75-117">Click **File**, and then click **Close** to exit Internet Explorer.</span></span>  
  
9. <span data-ttu-id="58f75-118">按一下**啟動**，按一下 **執行**，型別**regedit**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="58f75-118">Click **Start**, click **Run**, type **regedit**, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="58f75-119">在「登錄編輯程式」中，瀏覽至下列登錄機碼：</span><span class="sxs-lookup"><span data-stu-id="58f75-119">In Registry Editor, navigate to the following registry key:</span></span>  
  
     <span data-ttu-id="58f75-120">**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SystemCertificates**</span><span class="sxs-lookup"><span data-stu-id="58f75-120">**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SystemCertificates**</span></span>  
  
11. <span data-ttu-id="58f75-121">確認**AddressBook**登錄區存在。</span><span class="sxs-lookup"><span data-stu-id="58f75-121">Verify that the **AddressBook** hive is present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58f75-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58f75-122">See Also</span></span>  
 [<span data-ttu-id="58f75-123">復原執行 BizTalk Server 的電腦</span><span class="sxs-lookup"><span data-stu-id="58f75-123">Recovering a Computer Running BizTalk Server</span></span>](../core/recovering-a-computer-running-biztalk-server.md)