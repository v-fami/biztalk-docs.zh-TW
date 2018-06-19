---
title: 如何備份主要密碼 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0841c52a-7b15-45f8-9900-f5c9e3abd90b
caps.latest.revision: 3
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 124c077d7a15a4938f94239518ad02c8268074a4
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "30250994"
---
# <a name="how-to-back-up-the-master-secret"></a><span data-ttu-id="1dc93-102">如何備份主要密碼</span><span class="sxs-lookup"><span data-stu-id="1dc93-102">How to Back Up the Master Secret</span></span>
<span data-ttu-id="1dc93-103">您可以從主要密碼伺服器將主要密碼備份至 NTFS 檔案系統或卸除式媒體 (例如磁片)。</span><span class="sxs-lookup"><span data-stu-id="1dc93-103">You can back up the master secret from the master secret server onto an NTFS file system or removable media, such as a floppy disk.</span></span>  
  
 <span data-ttu-id="1dc93-104">您必須是單一登入系統管理員和 Windows 系統管理員才能執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="1dc93-104">You must be a Single Sign-On administrator and a Windows administrator to perform this task.</span></span> <span data-ttu-id="1dc93-105">單一登入 (SSO) 系統會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="1dc93-105">The Single Sign-On (SSO) system will prompt you for a password.</span></span> <span data-ttu-id="1dc93-106">若以後要復原密碼，您必須指定相同密碼。</span><span class="sxs-lookup"><span data-stu-id="1dc93-106">To restore the secret later, you must specify the same password.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1dc93-107">如果主要密碼伺服器當機和遺失金鑰，或如果是金鑰損毀，您將無法擷取儲存在認證資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="1dc93-107">If the master secret server crashes and you lose the key, or if the key becomes corrupted, you will not be able to retrieve data stored in the Credential database.</span></span> <span data-ttu-id="1dc93-108">您必須備份主要密碼或您可能會遺失認證資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="1dc93-108">You must back up the master secret, or you risk losing data from the Credential database.</span></span>  
  
### <a name="to-back-up-the-master-secret-using-the-mmc-snap-in"></a><span data-ttu-id="1dc93-109">使用 MMC 嵌入式管理單元備份主要密碼</span><span class="sxs-lookup"><span data-stu-id="1dc93-109">To back up the master secret using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="1dc93-110">按一下**啟動**，指向 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="1dc93-110">Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="1dc93-111">在 ENTSSO Microsoft Management Console (MMC) 嵌入式管理單元的範圍窗格中，展開 **企業單一登入**節點。</span><span class="sxs-lookup"><span data-stu-id="1dc93-111">In the scope pane of the ENTSSO Microsoft Management Console (MMC) Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="1dc93-112">以滑鼠右鍵按一下**系統**，然後按一下 **備份主要密碼**。</span><span class="sxs-lookup"><span data-stu-id="1dc93-112">Right-click **System**, and then click **Back up Master Secret**.</span></span>  
  
### <a name="to-back-up-the-master-secret-using-the-command-line"></a><span data-ttu-id="1dc93-113">使用命令列備份主要密碼</span><span class="sxs-lookup"><span data-stu-id="1dc93-113">To back up the master secret using the command line</span></span>  
  
1.  <span data-ttu-id="1dc93-114">在**啟動**功能表上，按一下 **程式**，然後按一下 **附屬應用程式**。</span><span class="sxs-lookup"><span data-stu-id="1dc93-114">On the **Start** menu, click **Programs**, and then click **Accessories**.</span></span> <span data-ttu-id="1dc93-115">以滑鼠右鍵按一下 **命令提示字元**, ，然後按一下  **執行身分...**。</span><span class="sxs-lookup"><span data-stu-id="1dc93-115">Right-click **Command Prompt**, and then click **Run As…**.</span></span>  
  
2.  <span data-ttu-id="1dc93-116">選取適當的系統管理員，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="1dc93-116">Select the appropriate Administrator, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="1dc93-117">在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="1dc93-117">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="1dc93-118">預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="1dc93-118">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="1dc93-119">型別`ssoconfig –backupsecret <backup file>`，其中*\<備份檔案 >* 是其中的主要密碼將備份，例如，檔案的名稱與路徑`A:\ssobackup.bak`。</span><span class="sxs-lookup"><span data-stu-id="1dc93-119">Type `ssoconfig –backupsecret <backup file>`, where *\<backup file>* is the path and name of the file where the master secret will be backed up, for example, `A:\ssobackup.bak`.</span></span>  
  
5.  <span data-ttu-id="1dc93-120">提供密碼來保護這個檔案。</span><span class="sxs-lookup"><span data-stu-id="1dc93-120">Provide a password to help protect this file.</span></span>  
  
     <span data-ttu-id="1dc93-121">此時會提示您確認密碼，並輸入協助您記住此密碼的密碼提示。</span><span class="sxs-lookup"><span data-stu-id="1dc93-121">You will be prompted to confirm the password and to provide a password hint to help you remember this password.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1dc93-122">您必須將備份檔案儲存並存放在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="1dc93-122">You must save and store the backup file in a secure location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dc93-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dc93-123">See Also</span></span>  
 <span data-ttu-id="1dc93-124">[如何產生主要密碼](../esso/how-to-generate-the-master-secret.md) </span><span class="sxs-lookup"><span data-stu-id="1dc93-124">[How to Generate the Master Secret](../esso/how-to-generate-the-master-secret.md) </span></span>  
 <span data-ttu-id="1dc93-125">[如何還原主要密碼](../esso/how-to-restore-the-master-secret.md) </span><span class="sxs-lookup"><span data-stu-id="1dc93-125">[How to Restore the Master Secret](../esso/how-to-restore-the-master-secret.md) </span></span>  
 <span data-ttu-id="1dc93-126">[主要密碼伺服器](../esso/master-secret-server.md) </span><span class="sxs-lookup"><span data-stu-id="1dc93-126">[Master Secret Server](../esso/master-secret-server.md) </span></span>  
 [<span data-ttu-id="1dc93-127">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="1dc93-127">Managing the Master Secret</span></span>](../esso/managing-the-master-secret.md)