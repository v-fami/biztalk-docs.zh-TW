---
title: 如何產生主要祕密 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Master Secret server, generating
- managing [Master Secret server], generating
ms.assetid: 5512a8ee-bc5b-4fe4-90c7-41e3baaa723b
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41e7f000dbb53a054259ba18f5c1d118531c8138
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978335"
---
# <a name="how-to-generate-the-master-secret"></a><span data-ttu-id="76a4e-102">如何產生主要密碼</span><span class="sxs-lookup"><span data-stu-id="76a4e-102">How to Generate the Master Secret</span></span>
<span data-ttu-id="76a4e-103">您必須具有主要密碼伺服器的管理權限，才可以執行此工作。</span><span class="sxs-lookup"><span data-stu-id="76a4e-103">You must have administrator rights on the master secret server in order to perform this task.</span></span> <span data-ttu-id="76a4e-104">此外，您必須從主要密碼伺服器執行此工作。</span><span class="sxs-lookup"><span data-stu-id="76a4e-104">In addition, you must perform this task from the master secret server.</span></span>  
  
 <span data-ttu-id="76a4e-105">您安裝「企業單一登入」的第一台伺服器會變成主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="76a4e-105">The first server where you install Enterprise Single Sign-On becomes the master secret server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="76a4e-106">SSO 系統中只能有一台主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="76a4e-106">There can be only one master secret server in your SSO system.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="76a4e-107">當「企業單一登入」是安裝為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝的一部分時，則會由組態精靈產生主要密碼。</span><span class="sxs-lookup"><span data-stu-id="76a4e-107">When Enterprise Single Sign-On is installed as part of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation, the master secret is generated as part of the Configuration Wizard.</span></span> <span data-ttu-id="76a4e-108">若您想要產生新的主要密碼，只需執行此工作即可。</span><span class="sxs-lookup"><span data-stu-id="76a4e-108">You will only need to perform this task if you want to generate a new master secret.</span></span>  
  
### <a name="to-generate-the-master-secret-using-the-mmc-snap-in"></a><span data-ttu-id="76a4e-109">使用 MMC 嵌入式管理單元產生主要密碼</span><span class="sxs-lookup"><span data-stu-id="76a4e-109">To generate the master secret using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="76a4e-110">在 **[開始]** 功能表上，依序按一下 **[所有程式]** 及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。</span><span class="sxs-lookup"><span data-stu-id="76a4e-110">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="76a4e-111">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="76a4e-111">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="76a4e-112">以滑鼠右鍵按一下**系統**，然後按一下**產生祕密**。</span><span class="sxs-lookup"><span data-stu-id="76a4e-112">Right-click **System**, and then click **Generate Secret**.</span></span>  
  
### <a name="to-generate-the-master-secret-using-the-command-line"></a><span data-ttu-id="76a4e-113">使用命令列產生主要密碼</span><span class="sxs-lookup"><span data-stu-id="76a4e-113">To generate the master secret using the command line</span></span>  
  
1.  <span data-ttu-id="76a4e-114">在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="76a4e-114">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="76a4e-115">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="76a4e-115">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="76a4e-116">預設的安裝目錄*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="76a4e-116">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="76a4e-117">型別**ssoconfig-generateSecret \<*備份檔案*\>**，其中\<*備份檔案*\>的名稱包含主要密碼的檔案。</span><span class="sxs-lookup"><span data-stu-id="76a4e-117">Type **ssoconfig –generateSecret \<*backup file*\>**, where \<*backup file*\> is the name of the file that contains the master secret.</span></span>  
  
     <span data-ttu-id="76a4e-118">系統會提示您輸入密碼，以保護剛建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="76a4e-118">You will be prompted to enter a password to protect the file you just created.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="76a4e-119">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="76a4e-119">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76a4e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76a4e-120">See Also</span></span>  
 <span data-ttu-id="76a4e-121">[如何備份主要密碼](../core/how-to-back-up-the-master-secret.md) </span><span class="sxs-lookup"><span data-stu-id="76a4e-121">[How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md) </span></span>  
 <span data-ttu-id="76a4e-122">[主要密碼伺服器](../core/master-secret-server.md) </span><span class="sxs-lookup"><span data-stu-id="76a4e-122">[Master Secret Server](../core/master-secret-server.md) </span></span>  
 [<span data-ttu-id="76a4e-123">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="76a4e-123">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)