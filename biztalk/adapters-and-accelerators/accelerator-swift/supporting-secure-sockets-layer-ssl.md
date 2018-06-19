---
title: 支援安全通訊端層 (SSL) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSL
ms.assetid: 012a5be0-bab8-4a60-9d63-b9684b91e4a7
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 086ec1715d76a25649cb2285b31b3df790b0fe3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214158"
---
# <a name="supporting-secure-sockets-layer-ssl"></a><span data-ttu-id="5af44-102">支援安全通訊端層 (SSL)</span><span class="sxs-lookup"><span data-stu-id="5af44-102">Supporting Secure Sockets Layer (SSL)</span></span>
<span data-ttu-id="5af44-103">若要實作安全通訊端層 (SSL) 通訊協定的用戶端電腦與 MRSR 伺服器之間部署中，您需要要求您的網際網路資訊服務 (IIS) 伺服器上設定 「 伺服器驗證 」 憑證。</span><span class="sxs-lookup"><span data-stu-id="5af44-103">To implement the Secure Sockets Layer (SSL) protocol in your deployment between the client computers and the MRSR servers, you need to request and configure a "Server Authentication" certificate on your Internet Information Services (IIS) servers.</span></span>  
  
 <span data-ttu-id="5af44-104">一個憑證應該用於網路負載平衡 (NLB) 叢集中的所有伺服器。</span><span class="sxs-lookup"><span data-stu-id="5af44-104">One certificate should be used for all the servers in your Network Load Balancing (NLB) cluster.</span></span> <span data-ttu-id="5af44-105">您應該確定在憑證要求中所使用的名稱是虛擬的主機名稱，而不是個別的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="5af44-105">You should ensure that the name used in the certificate request is the virtual host name instead of an individual server name.</span></span>