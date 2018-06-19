---
title: 如何將遠端使用者登入本機應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 886ee7cb-e6ba-476a-bea9-4bb4c22bf94e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f638007c3c4eb1f85a5b5a701dd2b456c2d220d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254214"
---
# <a name="how-to-log-a-remote-user-on-to-a-local-application"></a><span data-ttu-id="cf2c2-102">如何將遠端使用者登入本機應用程式</span><span class="sxs-lookup"><span data-stu-id="cf2c2-102">How to Log a Remote User on to a Local Application</span></span>
<span data-ttu-id="cf2c2-103">「企業單一登入」(ENTSSO) 服務的另一個主要功能是支援主控件初始化的程序 (HIP)。</span><span class="sxs-lookup"><span data-stu-id="cf2c2-103">The other main feature of Enterprise Single Sign-On service (ENTSSO) is supporting a host-initiated process (HIP).</span></span> <span data-ttu-id="cf2c2-104">當遠端使用者嘗試存取本機 Windows 資源時，ENTSSO 會與 HIP 互動。</span><span class="sxs-lookup"><span data-stu-id="cf2c2-104">ENTSSO interacts with HIP when a remote user tries to access a local Windows resource.</span></span> <span data-ttu-id="cf2c2-105">使用 ENTSSO 時，您可以接收來自主控件使用者的要求，以及對本機 Windows 應用程式的存取要求。</span><span class="sxs-lookup"><span data-stu-id="cf2c2-105">Using ENTSSO, you can receive the request from the host user and request access to the local Windows application.</span></span>  
  
## <a name="log-a-remote-user-on-to-a-local-windows-application"></a><span data-ttu-id="cf2c2-106">遠端使用者登入本機 Windows 應用程式</span><span class="sxs-lookup"><span data-stu-id="cf2c2-106">Log a remote user on to a local Windows application</span></span>  
  
1.  <span data-ttu-id="cf2c2-107">接收來自遠端使用者的要求。</span><span class="sxs-lookup"><span data-stu-id="cf2c2-107">Receive the request from the remote user.</span></span>  
  
     <span data-ttu-id="cf2c2-108">您必須決定如何接收遠端使用者的要求。</span><span class="sxs-lookup"><span data-stu-id="cf2c2-108">It is your responsibility to determine how to retrieve a request from the remote user.</span></span>  
  
2.  <span data-ttu-id="cf2c2-109">使用 `ISSOLookup2.LogonExternalUser` 要求授與遠端使用者存取指定之分支機構應用程式的權限。</span><span class="sxs-lookup"><span data-stu-id="cf2c2-109">Request that the remote user be given access to the specified affiliate application, using `ISSOLookup2.LogonExternalUser`.</span></span>  
  
     <span data-ttu-id="cf2c2-110">`LogonExternalUser` 會傳遞外部使用者希望存取的應用程式名稱、外部使用者名稱、外部使用者的相關認證，以及任何相關旗標。</span><span class="sxs-lookup"><span data-stu-id="cf2c2-110">`LogonExternalUser` passes in the name of the application the external user wishes to access, the name of the external user, the associated credentials for the external user, and any relevant flags.</span></span> <span data-ttu-id="cf2c2-111">如果成功的話，`LogonExternalUser` 會傳回 Windows 存取語彙基元的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="cf2c2-111">If successful, `LogonExternalUser` returns a handle to a Windows access token.</span></span>  
  
     <span data-ttu-id="cf2c2-112">遠端使用者必須已經通過「單一登入」資料庫中的識別、在此資料庫中具有認證，並與分支機構應用程式建立關聯。</span><span class="sxs-lookup"><span data-stu-id="cf2c2-112">The remote user must already be identified in the Single Sign-On database, have their credentials in the database, and be associated with an affiliate application.</span></span> <span data-ttu-id="cf2c2-113">否則，`LogonExternalUser` 會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="cf2c2-113">Otherwise, `LogonExternalUser` returns an error.</span></span> <span data-ttu-id="cf2c2-114">您可以使用「密碼同步」讓使用者名稱和認證保持在最新的狀態。</span><span class="sxs-lookup"><span data-stu-id="cf2c2-114">You can keep the user names and credentials up to date using Password Sync.</span></span>  
  
     <span data-ttu-id="cf2c2-115">另外，您也必須啟用通訊協定轉換。</span><span class="sxs-lookup"><span data-stu-id="cf2c2-115">In addition, you must have protocol transition enabled.</span></span>  
  
3.  <span data-ttu-id="cf2c2-116">使用 `LogonExternalUser` 傳回的 Windows 控制代碼來模擬此語彙基元所代表的使用者。</span><span class="sxs-lookup"><span data-stu-id="cf2c2-116">Use the Windows handle returned from `LogonExternalUser` to impersonate the user that the token represents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf2c2-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf2c2-117">See Also</span></span>  
 <span data-ttu-id="cf2c2-118">[如何登入非 Windows 應用程式的本機使用者](../core/how-to-log-a-local-user-on-to-a-non-windows-application.md) </span><span class="sxs-lookup"><span data-stu-id="cf2c2-118">[How to Log a Local User on to a Non-Windows Application](../core/how-to-log-a-local-user-on-to-a-non-windows-application.md) </span></span>  
 <span data-ttu-id="cf2c2-119">**ISSOLookup2.LogonExternalUser 方法**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="cf2c2-119">**ISSOLookup2.LogonExternalUser Method** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>