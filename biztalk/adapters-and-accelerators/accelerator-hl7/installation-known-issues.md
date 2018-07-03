---
title: 安裝已知問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b2f80ff9-b37c-49f8-8250-fcf3cec4c0fc
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f017fa273d91d1c40727ba34c6d047383054d52
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000919"
---
# <a name="installation-known-issues"></a><span data-ttu-id="ca23f-102">安裝已知問題</span><span class="sxs-lookup"><span data-stu-id="ca23f-102">Installation known issues</span></span>
<span data-ttu-id="ca23f-103">有用的資訊可協助您避免安裝問題。</span><span class="sxs-lookup"><span data-stu-id="ca23f-103">Useful information that may help you avoid installation problems.</span></span>  
  
## <a name="prerequisites-for-installing-btahl7"></a><span data-ttu-id="ca23f-104">安裝 BTAHL7 的必要條件</span><span class="sxs-lookup"><span data-stu-id="ca23f-104">Prerequisites for installing BTAHL7</span></span>  
 <span data-ttu-id="ca23f-105">安裝的先決條件[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="ca23f-105">The prerequisites for installing [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] include the following:</span></span>  
  
- <span data-ttu-id="ca23f-106">基本元件[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，包括企業單一登入 (SSO)、 群組和執行階段應該設定。</span><span class="sxs-lookup"><span data-stu-id="ca23f-106">Basic components of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], including Enterprise Single Sign-On (SSO), Group, and Runtime, should be configured.</span></span>  
  
- <span data-ttu-id="ca23f-107">安裝和設定 BTAHL7 使用者必須是 BizTalk 系統管理員群組的成員和儲存 BTAHL7 資料的 SQL Server 上的 Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="ca23f-107">The user installing and configuring BTAHL7 must be a member of the BizTalk Administrators group, and a member of the Administrators group on the SQL Server where the BTAHL7 data is stored.</span></span>
  
## <a name="sql-server-mixed-mode-not-supported"></a><span data-ttu-id="ca23f-108">不支援的 SQL Server 混合的模式</span><span class="sxs-lookup"><span data-stu-id="ca23f-108">SQL Server mixed mode not supported</span></span>  
<span data-ttu-id="ca23f-109">[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]不支援混合模式中的 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="ca23f-109">The [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] does not support SQL Server in mixed mode.</span></span>  
  
## <a name="repair-does-not-work-from-uninstallchange"></a><span data-ttu-id="ca23f-110">修復無法解除安裝/變更程式運作</span><span class="sxs-lookup"><span data-stu-id="ca23f-110">Repair does not work from uninstall/change</span></span>  
<span data-ttu-id="ca23f-111">如果已啟用使用者存取控制 (UAC)，而且您嘗試修復您使用控制台中的安裝，修復就會失敗。</span><span class="sxs-lookup"><span data-stu-id="ca23f-111">If user access control (UAC) is enabled, and you try to repair your installation using the control panel, the repair fails.</span></span> 

<span data-ttu-id="ca23f-112">Microsoft 建議您持續啟用 UAC。</span><span class="sxs-lookup"><span data-stu-id="ca23f-112">Microsoft recommends you keep UAC enabled.</span></span>

 <span data-ttu-id="ca23f-113">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="ca23f-113">**Resolution**</span></span>  
  
 <span data-ttu-id="ca23f-114">執行[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]setup.exe，然後選取**修復**。</span><span class="sxs-lookup"><span data-stu-id="ca23f-114">Run the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] setup.exe, and then select **Repair**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca23f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca23f-115">See Also</span></span>  
[<span data-ttu-id="ca23f-116">安裝或升級 Microsoft BizTalk Accelerator for HL7</span><span class="sxs-lookup"><span data-stu-id="ca23f-116">Install or upgrade Microsoft BizTalk Accelerator for HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/install-or-upgrade-microsoft-biztalk-accelerator-for-hl7.md)