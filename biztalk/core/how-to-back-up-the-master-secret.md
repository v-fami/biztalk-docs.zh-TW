---
title: 如何備份主要密碼 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [Master Secret server], backing up
- backing up, Master Secret server
- Master Secret server, backing up
ms.assetid: 22c23f66-b7df-4379-8a9f-065406ba8aa8
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 185f3ea674015e02cac2bdaa785c2ee06e67db65
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-back-up-the-master-secret"></a><span data-ttu-id="28190-102">如何備份主要密碼</span><span class="sxs-lookup"><span data-stu-id="28190-102">How to Back Up the Master Secret</span></span>
<span data-ttu-id="28190-103">您可以從主要密碼伺服器將主要密碼備份至 NTFS 檔案系統或卸除式媒體 (例如磁片)。</span><span class="sxs-lookup"><span data-stu-id="28190-103">You can back up the master secret from the master secret server onto an NTFS file system or removable media, such as a floppy disk.</span></span>  
  
 <span data-ttu-id="28190-104">您必須是「單一登入管理員」和 Windows 系統管理員才能執行此作業。</span><span class="sxs-lookup"><span data-stu-id="28190-104">You must be a Single Sign-On Administrator and a Windows administrator to perform this task.</span></span> <span data-ttu-id="28190-105">SSO 系統會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="28190-105">The SSO system will prompt you for a password.</span></span> <span data-ttu-id="28190-106">若以後要復原密碼，您必須指定相同密碼。</span><span class="sxs-lookup"><span data-stu-id="28190-106">To restore the secret later, you must specify the same password.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="28190-107">若主要密碼伺服器失敗且遺失金鑰，或者是金鑰損毀，您將無法擷取儲存在 SSO 資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="28190-107">If the master secret server fails and you lose the key, or if the key becomes corrupted, you will not be able to retrieve data stored in the SSO database.</span></span> <span data-ttu-id="28190-108">您必須備份主要密碼，否則會有遺失 SSO 資料庫資料的風險。</span><span class="sxs-lookup"><span data-stu-id="28190-108">You must back up the master secret, or you risk losing data from the SSO database.</span></span>  
  
### <a name="to-back-up-the-master-secret-using-the-mmc-snap-in"></a><span data-ttu-id="28190-109">使用 MMC 嵌入式管理單元備份主要密碼</span><span class="sxs-lookup"><span data-stu-id="28190-109">To back up the master secret using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="28190-110">在 **[開始]** 功能表上，依序按一下 **[所有程式]**及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。</span><span class="sxs-lookup"><span data-stu-id="28190-110">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="28190-111">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="28190-111">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="28190-112">以滑鼠右鍵按一下 **系統**, ，然後按一下  **備份密碼**。</span><span class="sxs-lookup"><span data-stu-id="28190-112">Right-click **System**, and then click **Backup Secret**.</span></span>  
  
### <a name="to-back-up-the-master-secret-using-the-command-line"></a><span data-ttu-id="28190-113">使用命令列備份主要密碼</span><span class="sxs-lookup"><span data-stu-id="28190-113">To back up the master secret using the command line</span></span>  
  
1.  <span data-ttu-id="28190-114">在 **啟動**  功能表上，按一下  **所有程式**, ，然後按一下  **附屬應用程式**。</span><span class="sxs-lookup"><span data-stu-id="28190-114">On the **Start** menu, click **All Programs**, and then click **Accessories**.</span></span> <span data-ttu-id="28190-115">以滑鼠右鍵按一下 **命令提示字元**, ，然後按一下  **執行身分...**。</span><span class="sxs-lookup"><span data-stu-id="28190-115">Right-click **Command Prompt**, and then click **Run As…**.</span></span>  
  
2.  <span data-ttu-id="28190-116">選取適當的系統管理員，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="28190-116">Select the appropriate Administrator, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="28190-117">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="28190-117">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="28190-118">預設安裝目錄是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="28190-118">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="28190-119">型別 * * ssoconfig – backupSecret *\<備份檔案\>* * *，其中*\<備份檔案\>*是其中的主要密碼將備份的檔案的名稱與路徑。</span><span class="sxs-lookup"><span data-stu-id="28190-119">Type **ssoconfig –backupSecret *\<backup file\>***, where *\<backup file\>* is the path and name of the file where the master secret will be backed up.</span></span> <span data-ttu-id="28190-120">例如，A:\ssobackup.bak</span><span class="sxs-lookup"><span data-stu-id="28190-120">For example, A:\ssobackup.bak</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="28190-121">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="28190-121">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
5.  <span data-ttu-id="28190-122">輸入用來保護此檔案的密碼。</span><span class="sxs-lookup"><span data-stu-id="28190-122">Provide a password to protect this file.</span></span> <span data-ttu-id="28190-123">此時會提示您確認密碼，並輸入協助您記住此密碼的密碼提示。</span><span class="sxs-lookup"><span data-stu-id="28190-123">You will be prompted to confirm the password and to provide a password hint to help you remember this password.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="28190-124">您必須將備份檔案儲存並存放在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="28190-124">You must save and store the backup file in a secure location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28190-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28190-125">See Also</span></span>  
 <span data-ttu-id="28190-126">[如何產生主要密碼](../core/how-to-generate-the-master-secret.md) </span><span class="sxs-lookup"><span data-stu-id="28190-126">[How to Generate the Master Secret](../core/how-to-generate-the-master-secret.md) </span></span>  
 <span data-ttu-id="28190-127">[如何還原主要密碼](../core/how-to-restore-the-master-secret.md) </span><span class="sxs-lookup"><span data-stu-id="28190-127">[How to Restore the Master Secret](../core/how-to-restore-the-master-secret.md) </span></span>  
 <span data-ttu-id="28190-128">[主要密碼伺服器](../core/master-secret-server.md) </span><span class="sxs-lookup"><span data-stu-id="28190-128">[Master Secret Server](../core/master-secret-server.md) </span></span>  
 [<span data-ttu-id="28190-129">管理主要密碼</span><span class="sxs-lookup"><span data-stu-id="28190-129">Managing the Master Secret</span></span>](../core/managing-the-master-secret.md)