---
title: 傳訊引擎介面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 14241db3-edcf-4449-9ec8-2171a14496c0
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a135505240e94fb42e5810a3e7ac71d4c99c34a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263286"
---
# <a name="messaging-engine-interfaces"></a><span data-ttu-id="3bae7-102">傳訊引擎介面</span><span class="sxs-lookup"><span data-stu-id="3bae7-102">Messaging Engine Interfaces</span></span>
<span data-ttu-id="3bae7-103">有三個公用介面，可供配接器用來與傳訊引擎進行互動。</span><span class="sxs-lookup"><span data-stu-id="3bae7-103">There are three public interfaces that adapters can use to allow interaction with the Messaging Engine.</span></span> <span data-ttu-id="3bae7-104">下列章節中將說明這些介面。</span><span class="sxs-lookup"><span data-stu-id="3bae7-104">These are outlined in the following sections.</span></span>  
  
## <a name="ibttransportproxy"></a><span data-ttu-id="3bae7-105">IBTTransportProxy</span><span class="sxs-lookup"><span data-stu-id="3bae7-105">IBTTransportProxy</span></span>  
 <span data-ttu-id="3bae7-106">配接器永遠都會使用自己的傳輸 Proxy 來和傳訊引擎互動。</span><span class="sxs-lookup"><span data-stu-id="3bae7-106">Adapters always interact with the Messaging Engine by using their own transport proxy.</span></span> <span data-ttu-id="3bae7-107">傳輸 Proxy 會用於建立批次、取得訊息 Factory、向引擎註冊外掛式接收器等作業。</span><span class="sxs-lookup"><span data-stu-id="3bae7-107">The transport proxy is used for operations such as creating batches, getting the message factory, and registering isolated receivers with the engine.</span></span>  
  
## <a name="ibttransportbatch"></a><span data-ttu-id="3bae7-108">IBTTransportBatch</span><span class="sxs-lookup"><span data-stu-id="3bae7-108">IBTTransportBatch</span></span>  
 <span data-ttu-id="3bae7-109">此介面是由傳訊引擎提供，它定義配接器可用來操作訊息批次的方法。</span><span class="sxs-lookup"><span data-stu-id="3bae7-109">This interface is provided by the Messaging Engine, and defines methods that adapters can use to operate on batches of messages.</span></span> <span data-ttu-id="3bae7-110">傳訊引擎會以非同步方式處理批次。</span><span class="sxs-lookup"><span data-stu-id="3bae7-110">The Messaging Engine processes batches asynchronously.</span></span>  
  
## <a name="ibtdtccommitconfirm"></a><span data-ttu-id="3bae7-111">IBTDTCCommitConfirm</span><span class="sxs-lookup"><span data-stu-id="3bae7-111">IBTDTCCommitConfirm</span></span>  
 <span data-ttu-id="3bae7-112">使用明確的 Microsoft Distributed Transaction Coordinator (MSDTC) 交易的配接器，必須使用此介面將使用此介面之交易的結果告知引擎。</span><span class="sxs-lookup"><span data-stu-id="3bae7-112">Adapters using explicit Microsoft Distributed Transaction Coordinator (MSDTC) transactions on batches must use this interface to notify the engine of the outcome of the transaction using this interface.</span></span>