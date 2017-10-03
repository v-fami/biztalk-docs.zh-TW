---
title: "如何使用直接密碼同步 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1334c2f-2020-46ea-a98c-f7688813e38c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6080589271d845432e875cb335a2ef354c9784ca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-direct-password-sync"></a><span data-ttu-id="f8121-102">如何使用直接密碼同步</span><span class="sxs-lookup"><span data-stu-id="f8121-102">How to Use Direct Password Sync</span></span>
<span data-ttu-id="f8121-103">本版本的「企業單一登入」包含「直接從 Windows 進行密碼同步」的功能。</span><span class="sxs-lookup"><span data-stu-id="f8121-103">This version of Enterprise Single Sign-On includes the Direct Password Sync from Windows feature.</span></span> <span data-ttu-id="f8121-104">這項功能可讓您略過「密碼同步配接器」，而直接從 Windows 更新「SSO 資料庫」中的密碼。</span><span class="sxs-lookup"><span data-stu-id="f8121-104">This enables you to bypass a Password Sync Adapter and update the password in the SSO Database directly from Windows.</span></span>  
  
 <span data-ttu-id="f8121-105">下列為可以使用「直接從 Windows 進行密碼同步」的情況：</span><span class="sxs-lookup"><span data-stu-id="f8121-105">Direct Password Sync from Windows is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="f8121-106">您的企業系統需要 Windows 到 Windows 對應。</span><span class="sxs-lookup"><span data-stu-id="f8121-106">Your enterprise system requires Windows to Windows mapping.</span></span>  
  
-   <span data-ttu-id="f8121-107">當 Windows 使用者發生密碼變更時，您必須直接在 SSO 資料庫中更新相關的外部使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="f8121-107">You need to update the External User’s password in the SSO database directly when a password change occurs for the Windows user.</span></span> <span data-ttu-id="f8121-108">您可以透過其他的機制，變更後端系統上的密碼 (其對應到該外部使用者)。</span><span class="sxs-lookup"><span data-stu-id="f8121-108">You can change the password on the back-end system (that corresponds to the external user) by using other mechanisms.</span></span> <span data-ttu-id="f8121-109">例如，您可以使用 Microsoft Identity Integration Server，更新 IBM 主機上應用 RACF 管理代理程式之「資源存取控制設施」(Resource Access Control Facility，RACF) 中的密碼。</span><span class="sxs-lookup"><span data-stu-id="f8121-109">For example, you can use Microsoft Identity Integration Server to update passwords in Resource Access Control Facility (RACF) on an IBM Mainframe using the RACF Management Agent.</span></span>  
  
### <a name="to-enable-direct-password-sync"></a><span data-ttu-id="f8121-110">若要啟用直接密碼同步</span><span class="sxs-lookup"><span data-stu-id="f8121-110">To enable Direct Password Sync</span></span>  
  
1.  <span data-ttu-id="f8121-111">開啟 [企業單一登入]。</span><span class="sxs-lookup"><span data-stu-id="f8121-111">Open Enterprise Single Sign-On.</span></span>  
  
2.  <span data-ttu-id="f8121-112">在 [領域] 窗格中，按一下**分支機構應用程式**。</span><span class="sxs-lookup"><span data-stu-id="f8121-112">In the scope pane, click **Affiliate Applications**.</span></span>  
  
3.  <span data-ttu-id="f8121-113">以滑鼠右鍵按一下適當**分支機構應用程式**。</span><span class="sxs-lookup"><span data-stu-id="f8121-113">Right-click the appropriate **Affiliate Application**.</span></span>  
  
4.  <span data-ttu-id="f8121-114">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="f8121-114">Click **Properties**.</span></span>  
  
     <span data-ttu-id="f8121-115">**分支機構應用程式屬性** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="f8121-115">The **Affiliate Applications Properties** dialog box appears.</span></span>  
  
5.  <span data-ttu-id="f8121-116">按一下**選項** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f8121-116">Click the **Options** tab.</span></span>  
  
6.  <span data-ttu-id="f8121-117">選取**直接從 Windows 進行密碼同步**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f8121-117">Select the **Direct Password Sync from Windows** check box.</span></span>  
  
7.  <span data-ttu-id="f8121-118">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f8121-118">Click **OK**.</span></span>