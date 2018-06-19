---
title: 安裝憑證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates, installing
- installing, certificates
ms.assetid: 7525f771-623c-420f-99ca-c834e819829d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5ded26548303dfe9c9a095c24396b4e2683ca4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209462"
---
# <a name="installing-certificates"></a><span data-ttu-id="63434-102">安裝憑證</span><span class="sxs-lookup"><span data-stu-id="63434-102">Installing Certificates</span></span>
<span data-ttu-id="63434-103">若要傳送、 修復或提交訊息，您必須安裝適當的認證。</span><span class="sxs-lookup"><span data-stu-id="63434-103">To send, repair, or submit messages, you must have the proper certificates installed.</span></span> <span data-ttu-id="63434-104">本主題描述如何加入憑證。</span><span class="sxs-lookup"><span data-stu-id="63434-104">This topic describes how to add certificates.</span></span> <span data-ttu-id="63434-105">在實際執行環境中，請參閱您 IT 部門以取得憑證。</span><span class="sxs-lookup"><span data-stu-id="63434-105">In a production environment, see your IT department for certificates.</span></span>  
  
 <span data-ttu-id="63434-106">**摘要**</span><span class="sxs-lookup"><span data-stu-id="63434-106">**Summary**</span></span>  
  
 <span data-ttu-id="63434-107">本節提供有關如何建立及儲存下列憑證的指示：</span><span class="sxs-lookup"><span data-stu-id="63434-107">This section provides instructions on how to create and store the following certificates:</span></span>  
  
-   <span data-ttu-id="63434-108">每個用戶端電腦上的每個訊息修復和新送出憑證-目前使用者的個人資料夾中的角色的憑證存放區</span><span class="sxs-lookup"><span data-stu-id="63434-108">Certificates for each of the Message Repair and New Submission roles in the Personal folder of the Certificates - Current User store on each client computer</span></span>  
  
-   <span data-ttu-id="63434-109">每個 BizTalk 協調流程伺服器電腦上的每個訊息修復和新送出憑證 （本機電腦） 的其他人資料夾中的角色的憑證存放區</span><span class="sxs-lookup"><span data-stu-id="63434-109">Certificates for each of the Message Repair and New Submission roles in the Other People folder of the Certificates (Local Computer) store on each BizTalk orchestration server computer</span></span>  
  
-   <span data-ttu-id="63434-110">憑證授權單位的憑證到信任的根憑證授權單位資料夾中每個用戶端電腦上的憑證 （本機電腦） 存放區</span><span class="sxs-lookup"><span data-stu-id="63434-110">Certification Authority's certificate into the Trusted Root Certification Authorities folder in the Certificates (Local Computer) store on each client computer</span></span>  
  
 <span data-ttu-id="63434-111">如果您已部署[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]的單一電腦上，也有相同的電腦上安裝的憑證伺服器，您要排除的受管理的路徑中的憑證伺服器[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]SharePoint 伺服器。</span><span class="sxs-lookup"><span data-stu-id="63434-111">If you have deployed [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] on a single computer, and also have a certificate server installed on the same computer, you need to exclude the certificate server from the managed paths for [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] SharePoint Server.</span></span>  
  
 <span data-ttu-id="63434-112">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="63434-112">This section contains:</span></span>  
  
-   [<span data-ttu-id="63434-113">將憑證新增至用戶端的憑證存放區</span><span class="sxs-lookup"><span data-stu-id="63434-113">Adding Certificates to the Certificates Store on the Client</span></span>](../../adapters-and-accelerators/accelerator-swift/adding-certificates-to-the-certificates-store-on-the-client.md)  
  
-   [<span data-ttu-id="63434-114">將憑證新增到伺服器的憑證存放區</span><span class="sxs-lookup"><span data-stu-id="63434-114">Adding Certificates to the Certificates Store on the Server</span></span>](../../adapters-and-accelerators/accelerator-swift/adding-certificates-to-the-certificates-store-on-the-server.md)  
  
-   [<span data-ttu-id="63434-115">從單一電腦部署受管理的路徑排除 CertSrv</span><span class="sxs-lookup"><span data-stu-id="63434-115">Excluding CertSrv from Managed Paths on a Single-Computer Deployment</span></span>](../../adapters-and-accelerators/accelerator-swift/excluding-certsrv-from-managed-paths-on-a-single-computer-deployment.md)