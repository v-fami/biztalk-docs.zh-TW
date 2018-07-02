---
title: 單一登入： 事件 10683 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 83cd1b96-cd79-4ddc-952b-94a7de216666
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a8a769e9cf74a3d0119ca814d7201c1e14e7304
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978303"
---
# <a name="single-sign-on-event-10683"></a><span data-ttu-id="9fc05-102">單一登入： 事件 10683</span><span class="sxs-lookup"><span data-stu-id="9fc05-102">Single Sign-On: Event 10683</span></span>
## <a name="details"></a><span data-ttu-id="9fc05-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9fc05-103">Details</span></span>  

|                 |                                                                          |
|-----------------|--------------------------------------------------------------------------|
|  <span data-ttu-id="9fc05-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9fc05-104">Product Name</span></span>   |                        <span data-ttu-id="9fc05-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="9fc05-105">Enterprise Single Sign-On</span></span>                         |
| <span data-ttu-id="9fc05-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="9fc05-106">Product Version</span></span> |        [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]        |
|    <span data-ttu-id="9fc05-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9fc05-107">Event ID</span></span>     |                                  <span data-ttu-id="9fc05-108">10683</span><span class="sxs-lookup"><span data-stu-id="9fc05-108">10683</span></span>                                   |
|  <span data-ttu-id="9fc05-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="9fc05-109">Event Source</span></span>   |                                  <span data-ttu-id="9fc05-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="9fc05-110">ENTSSO</span></span>                                  |
|    <span data-ttu-id="9fc05-111">元件</span><span class="sxs-lookup"><span data-stu-id="9fc05-111">Component</span></span>    |                                   <span data-ttu-id="9fc05-112">N\A</span><span class="sxs-lookup"><span data-stu-id="9fc05-112">N\A</span></span>                                    |
|  <span data-ttu-id="9fc05-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9fc05-113">Symbolic Name</span></span>  |                   <span data-ttu-id="9fc05-114">SSO_WARN_REPLAY_FILE_DELETED_TOO_OLD</span><span class="sxs-lookup"><span data-stu-id="9fc05-114">SSO_WARN_REPLAY_FILE_DELETED_TOO_OLD</span></span>                   |
|  <span data-ttu-id="9fc05-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9fc05-115">Message Text</span></span>   | <span data-ttu-id="9fc05-116">重新執行檔案已刪除，因為它太 old.%r</span><span class="sxs-lookup"><span data-stu-id="9fc05-116">A replay file was deleted because it was too old.%r</span></span><br /><span data-ttu-id="9fc05-117">重新執行檔案： %1</span><span class="sxs-lookup"><span data-stu-id="9fc05-117">Replay File: %1</span></span> |

## <a name="explanation"></a><span data-ttu-id="9fc05-118">說明</span><span class="sxs-lookup"><span data-stu-id="9fc05-118">Explanation</span></span>  
 <span data-ttu-id="9fc05-119">這個警告事件表示已刪除重新執行檔案，因為它太舊。</span><span class="sxs-lookup"><span data-stu-id="9fc05-119">This Warning event indicates that the replay file was deleted because it was too old.</span></span> <span data-ttu-id="9fc05-120">ENTSSO 伺服器無法連絡 SSO 資料庫時，密碼同步處理會使用重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="9fc05-120">Replay files are used by password sync when the ENTSSO server cannot contact the SSO database.</span></span> <span data-ttu-id="9fc05-121">在此案例中，密碼變更會儲存在暫時加密檔案，並且會在可用時重新執行回 SSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9fc05-121">In this case the password changes are stored in a temporary encrypted file and are replayed back to the SSO database when it again becomes available.</span></span> <span data-ttu-id="9fc05-122">可以將檔案重新執行回 SSO 資料庫時，如果檔案經偵測已經太舊，則會遭到捨棄。</span><span class="sxs-lookup"><span data-stu-id="9fc05-122">When it is time to replay the files back to the SSO database, if a file is detected that is too old, it is discarded.</span></span> <span data-ttu-id="9fc05-123">SSO 密碼同步系統會捨棄所有舊的密碼變更`password sync age`參數會決定密碼最長使用期限變更要求和，可以使用命令列工具來控制**ssoconfig – syncAge**或 SSO 管理 MMC。</span><span class="sxs-lookup"><span data-stu-id="9fc05-123">All old password changes are discarded by the SSO password sync system; the `password sync age` parameter determines the maximum age for password change requests and that can be controlled using the command line tools **ssoconfig –syncAge** or the SSO Admin MMC.</span></span>  

## <a name="user-action"></a><span data-ttu-id="9fc05-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9fc05-124">User Action</span></span>  

- <span data-ttu-id="9fc05-125">使用者不必採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="9fc05-125">No user action is necessary.</span></span>  

  <span data-ttu-id="9fc05-126">如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：</span><span class="sxs-lookup"><span data-stu-id="9fc05-126">For more information, see the following resources in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help:</span></span>  

- [<span data-ttu-id="9fc05-127">如何設定密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="9fc05-127">How to Configure Password Synchronization</span></span>](../core/how-to-configure-password-synchronization.md)  

- [<span data-ttu-id="9fc05-128">密碼同步</span><span class="sxs-lookup"><span data-stu-id="9fc05-128">Password Synchronization</span></span>](../core/password-synchronization2.md)
