---
title: 安裝憑證 |Microsoft Docs
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
ms.openlocfilehash: 111bd267bc7d0bc12d582c3b74846b8874ed8b4d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012543"
---
# <a name="installing-certificates"></a><span data-ttu-id="b1ab0-102">安裝憑證</span><span class="sxs-lookup"><span data-stu-id="b1ab0-102">Installing Certificates</span></span>
<span data-ttu-id="b1ab0-103">若要傳送、 修復或提交訊息，您必須安裝適當的認證。</span><span class="sxs-lookup"><span data-stu-id="b1ab0-103">To send, repair, or submit messages, you must have the proper certificates installed.</span></span> <span data-ttu-id="b1ab0-104">本主題描述如何新增憑證。</span><span class="sxs-lookup"><span data-stu-id="b1ab0-104">This topic describes how to add certificates.</span></span> <span data-ttu-id="b1ab0-105">在生產環境中，請參閱您的 IT 部門的憑證。</span><span class="sxs-lookup"><span data-stu-id="b1ab0-105">In a production environment, see your IT department for certificates.</span></span>  

 <span data-ttu-id="b1ab0-106">**摘要**</span><span class="sxs-lookup"><span data-stu-id="b1ab0-106">**Summary**</span></span>  

 <span data-ttu-id="b1ab0-107">本節說明如何建立並儲存下列憑證：</span><span class="sxs-lookup"><span data-stu-id="b1ab0-107">This section provides instructions on how to create and store the following certificates:</span></span>  

- <span data-ttu-id="b1ab0-108">每個用戶端電腦上將 Message Repair 和 New Submission 角色憑證-目前使用者的個人資料夾中的每個憑證存放區</span><span class="sxs-lookup"><span data-stu-id="b1ab0-108">Certificates for each of the Message Repair and New Submission roles in the Personal folder of the Certificates - Current User store on each client computer</span></span>  

- <span data-ttu-id="b1ab0-109">每個 BizTalk 協調流程伺服器電腦上將 Message Repair 和 New Submission 角色的憑證 （本機電腦） 的其他人 資料夾中的每個憑證存放區</span><span class="sxs-lookup"><span data-stu-id="b1ab0-109">Certificates for each of the Message Repair and New Submission roles in the Other People folder of the Certificates (Local Computer) store on each BizTalk orchestration server computer</span></span>  

- <span data-ttu-id="b1ab0-110">憑證授權單位憑證在每個用戶端電腦上的 Certificates (Local Computer) 存放區中的 [受信任的根憑證授權單位] 資料夾</span><span class="sxs-lookup"><span data-stu-id="b1ab0-110">Certification Authority's certificate into the Trusted Root Certification Authorities folder in the Certificates (Local Computer) store on each client computer</span></span>  

  <span data-ttu-id="b1ab0-111">如果您已部署[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]的單一電腦上，也可以安裝在同一部電腦上的憑證伺服器，您需要從受管理的路徑排除憑證伺服器，適用於 Microsoft SharePoint Server。</span><span class="sxs-lookup"><span data-stu-id="b1ab0-111">If you have deployed [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] on a single computer, and also have a certificate server installed on the same computer, you need to exclude the certificate server from the managed paths for Microsoft SharePoint Server.</span></span>  

  <span data-ttu-id="b1ab0-112">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="b1ab0-112">This section contains:</span></span>  

- [<span data-ttu-id="b1ab0-113">將憑證新增至用戶端上的憑證存放區</span><span class="sxs-lookup"><span data-stu-id="b1ab0-113">Adding Certificates to the Certificates Store on the Client</span></span>](../../adapters-and-accelerators/accelerator-swift/adding-certificates-to-the-certificates-store-on-the-client.md)  

- [<span data-ttu-id="b1ab0-114">將憑證新增至伺服器上的憑證存放區</span><span class="sxs-lookup"><span data-stu-id="b1ab0-114">Adding Certificates to the Certificates Store on the Server</span></span>](../../adapters-and-accelerators/accelerator-swift/adding-certificates-to-the-certificates-store-on-the-server.md)  

- [<span data-ttu-id="b1ab0-115">從單一電腦部署的受管理路徑中排除 CertSrv</span><span class="sxs-lookup"><span data-stu-id="b1ab0-115">Excluding CertSrv from Managed Paths on a Single-Computer Deployment</span></span>](../../adapters-and-accelerators/accelerator-swift/excluding-certsrv-from-managed-paths-on-a-single-computer-deployment.md)
