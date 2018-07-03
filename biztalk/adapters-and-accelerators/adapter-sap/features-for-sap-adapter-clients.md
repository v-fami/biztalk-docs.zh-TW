---
title: SAP 配接器用戶端的功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dynamic ports
- adapters, features
- XML data streaming
- performance counters
- adapters, support for dynamic ports in BizTalk Server
- adapters, support for message versioning
- adapters, support for XML data streaming
- adapters, support for performance counters
- adapters, support for configuring adapters using binding properties
ms.assetid: 9003c2c1-931d-405e-9a58-660032195af7
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 411ae3a1b044b89a0ef5390a0f0ad26430909bcb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984631"
---
# <a name="features-for-sap-adapter-clients"></a><span data-ttu-id="a4841-102">SAP 配接器用戶端的功能</span><span class="sxs-lookup"><span data-stu-id="a4841-102">Features for SAP adapter clients</span></span>
<span data-ttu-id="a4841-103">除了的主題所討論的功能之外[的 BizTalk Adapter for mySAP Business Suite 的架構概觀](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md)，則[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]也提供下列功能，可用於配接器用戶端。</span><span class="sxs-lookup"><span data-stu-id="a4841-103">In addition to the features discussed throughout the topics of [Architecture overview of BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md), the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] also provides the following features that are useful for adapter clients.</span></span>  
  
- <span data-ttu-id="a4841-104">**設定使用繫結屬性的配接器支援**。</span><span class="sxs-lookup"><span data-stu-id="a4841-104">**Support for configuring adapters using binding properties**.</span></span> <span data-ttu-id="a4841-105">配接器用戶端可以設定[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]藉由指定特定繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="a4841-105">Adapter clients can configure the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] by specifying certain binding properties.</span></span> <span data-ttu-id="a4841-106">例如，用戶端可以在其中設定配接器至配接器的連接集區中指定的連線數目上限，藉由指定的值**MaxConnectionsPerSystem**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="a4841-106">For example, clients can configure the adapter to specify the maximum number of connections in the adapter's connection pool by specifying a value for the **MaxConnectionsPerSystem** binding property.</span></span> <span data-ttu-id="a4841-107">如需詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="a4841-107">For more information, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
- <span data-ttu-id="a4841-108">**支援 BizTalk Server 中的動態連接埠**。</span><span class="sxs-lookup"><span data-stu-id="a4841-108">**Support for dynamic ports in BizTalk Server**.</span></span> <span data-ttu-id="a4841-109">透過 BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，則[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援動態連接埠，可讓您動態路由的訊息從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]根據訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="a4841-109">Through the BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports a dynamic port that enables dynamic routing of messages from [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] based on the message context properties.</span></span> <span data-ttu-id="a4841-110">如需詳細資訊，請參閱 <<c0> [ 設定動態連接埠](../../adapters-and-accelerators/adapter-sap/configure-dynamic-ports-in-the-sap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="a4841-110">For more information, see [Configure dynamic ports](../../adapters-and-accelerators/adapter-sap/configure-dynamic-ports-in-the-sap-adapter.md).</span></span>
  
- <span data-ttu-id="a4841-111">**訊息版本控制支援**。</span><span class="sxs-lookup"><span data-stu-id="a4841-111">**Support for message versioning**.</span></span> <span data-ttu-id="a4841-112">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援訊息版本控制，可啟用不同的訊息結構描述的未來版本中支援[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a4841-112">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports message versioning to enable support for different message schemas in future releases of the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="a4841-113">如需詳細資訊，請參閱 <<c0> [ 訊息版本控制支援](../../adapters-and-accelerators/adapter-sap/message-versioning-support1.md)。</span><span class="sxs-lookup"><span data-stu-id="a4841-113">For more information, see [Message Versioning Support](../../adapters-and-accelerators/adapter-sap/message-versioning-support1.md).</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="a4841-114">這項功能不提供與舊版配接器的回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="a4841-114">This feature does not provide backward compatibility with the earlier versions of the adapter.</span></span>  
  
- <span data-ttu-id="a4841-115">**對效能計數器支援**。</span><span class="sxs-lookup"><span data-stu-id="a4841-115">**Support for performance counters**.</span></span> <span data-ttu-id="a4841-116">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援配接器用戶端使用 wcf 效能計數器。</span><span class="sxs-lookup"><span data-stu-id="a4841-116">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports WCF-based performance counters for use by adapter clients.</span></span> <span data-ttu-id="a4841-117">如需有關效能計數器的詳細資訊，請參閱 <<c0> [ 與 SAP 配接器的使用效能計數器](../../adapters-and-accelerators/adapter-sap/use-performance-counters-with-the-sap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="a4841-117">For more information about performance counters, see [Use Performance Counters with the SAP adapter](../../adapters-and-accelerators/adapter-sap/use-performance-counters-with-the-sap-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4841-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4841-118">See Also</span></span>  
 [<span data-ttu-id="a4841-119">BizTalk adapter for mySAP Business Suite 的架構概觀</span><span class="sxs-lookup"><span data-stu-id="a4841-119">Architecture overview of BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md)