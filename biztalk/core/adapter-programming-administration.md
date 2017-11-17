---
title: "配接器程式設計管理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 38563b3c-6d52-4e4e-ac6e-74f46ce22c6a
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b19e3285357bb067614aae9472eb099470fe27f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-programming-administration"></a><span data-ttu-id="dd8c9-102">配接器程式設計管理</span><span class="sxs-lookup"><span data-stu-id="dd8c9-102">Adapter Programming Administration</span></span>
<span data-ttu-id="dd8c9-103">配接器是一種特殊的組態存放區應用程式： 也就是配接器是與其他單一登入和組態存放區應用程式共用命名空間的元件。</span><span class="sxs-lookup"><span data-stu-id="dd8c9-103">An adapter is a special type of configuration store application: that is, an adapter is a component that shares a namespace with other Single Sign-On and configuration store applications.</span></span> <span data-ttu-id="dd8c9-104">因此，您可以使用 ISSOConfigStore 存取配接器的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dd8c9-104">Therefore, you can access information about an adapter using ISSOConfigStore.</span></span> <span data-ttu-id="dd8c9-105">不過，與組態存放區應用程式不同的是，您不能在具有 ISSOAdmin 介面的配接器上執行管理功能。</span><span class="sxs-lookup"><span data-stu-id="dd8c9-105">But unlike a configuration store application, you do not perform administrative functions on an adapter with the ISSOAdmin interface.</span></span> <span data-ttu-id="dd8c9-106">而是必須透過 ISSOPSAdmin 管理配接器。</span><span class="sxs-lookup"><span data-stu-id="dd8c9-106">Instead, you administer an adapter through ISSOPSAdmin.</span></span> <span data-ttu-id="dd8c9-107">使用特定的配接器管理介面的原因是可讓系統為其他活動與組態存放區取得協調。</span><span class="sxs-lookup"><span data-stu-id="dd8c9-107">The reason for a specialized adapter administration interface is so that the system can coordinate other activities with the configuration store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd8c9-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd8c9-108">See Also</span></span>  
 <span data-ttu-id="dd8c9-109">[配接器程式設計組態](../core/adapter-programming-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="dd8c9-109">[Adapter Programming Configuration](../core/adapter-programming-configuration.md) </span></span>  
 <span data-ttu-id="dd8c9-110">[配接器群組和群組配接器](../core/adapter-groups-and-group-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="dd8c9-110">[Adapter Groups and Group Adapters](../core/adapter-groups-and-group-adapters.md) </span></span>  
 [<span data-ttu-id="dd8c9-111">密碼同步配接器</span><span class="sxs-lookup"><span data-stu-id="dd8c9-111">Password Sync Adapters</span></span>](../core/password-sync-adapters.md)