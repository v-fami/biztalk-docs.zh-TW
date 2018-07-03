---
title: 管理 Certificates1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing certificates
- certificates, managing
ms.assetid: ffa60e2b-c131-4a49-ad1e-6c8a7271b05c
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d9d326155ea788a77fe86c0c4eb126476d21ece
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984999"
---
# <a name="managing-certificates"></a><span data-ttu-id="163ab-102">管理憑證</span><span class="sxs-lookup"><span data-stu-id="163ab-102">Managing Certificates</span></span>
<span data-ttu-id="163ab-103">RosettaNet 中的安全通訊需要用到憑證。</span><span class="sxs-lookup"><span data-stu-id="163ab-103">Secure communications in RosettaNet require using certificates.</span></span> <span data-ttu-id="163ab-104">Microsoft®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]使用憑證來加密外寄訊息、 簽署外寄訊息、 解密內送訊息，並確認內送訊息中的簽章。</span><span class="sxs-lookup"><span data-stu-id="163ab-104">Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] uses certificates to encrypt outgoing messages, sign outgoing messages, decrypt incoming messages, and verify the signature in incoming messages.</span></span>  
  
 <span data-ttu-id="163ab-105">若要使用憑證，您必須執行下列部分或全部步驟：</span><span class="sxs-lookup"><span data-stu-id="163ab-105">To use certificates, you must perform some or all of the following steps:</span></span>  
  
-   <span data-ttu-id="163ab-106">將伺服器的憑證匯入憑證存放區</span><span class="sxs-lookup"><span data-stu-id="163ab-106">Import certificates into the certificates store for the server</span></span>  
  
-   <span data-ttu-id="163ab-107">設定憑證在訊息中的使用方式</span><span class="sxs-lookup"><span data-stu-id="163ab-107">Configure the use of certificates in messages</span></span>  
  
-   <span data-ttu-id="163ab-108">將憑證匯出給交易夥伴</span><span class="sxs-lookup"><span data-stu-id="163ab-108">Export certificates to partners</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="163ab-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="163ab-109">In This Section</span></span>  
  
-   [<span data-ttu-id="163ab-110">匯入憑證</span><span class="sxs-lookup"><span data-stu-id="163ab-110">Importing Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates.md)  
  
-   [<span data-ttu-id="163ab-111">匯出憑證</span><span class="sxs-lookup"><span data-stu-id="163ab-111">Exporting Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/exporting-certificates.md)