---
title: "設定 WCF 配接器攔截 BAM 資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd705c27-5d04-47e5-9bb2-61235f8fe544
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f418512ecd0a3e38f884965d1698579fb300dd74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-the-wcf-adapter-to-intercept-bam-data"></a><span data-ttu-id="aa06a-102">設定 WCF 配接器攔截 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="aa06a-102">Configuring the WCF Adapter to Intercept BAM Data</span></span>
<span data-ttu-id="aa06a-103">本節將針對您必須執行才可以將 BAM WCF 攔截器設定成配合 BAM WCF 攔截器執行的必要步驟，提供相關資訊。</span><span class="sxs-lookup"><span data-stu-id="aa06a-103">This section contains information about the steps you must take to configure the BizTalk WCF adapter to work with the BAM WCF interceptor.</span></span>  
  
 <span data-ttu-id="aa06a-104">基本步驟如下：</span><span class="sxs-lookup"><span data-stu-id="aa06a-104">The basic steps are as follows:</span></span>  
  
-   <span data-ttu-id="aa06a-105">將 BAM 行為加入至 machine.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="aa06a-105">Add the BAM behavior to the machine.config file.</span></span>  
  
-   <span data-ttu-id="aa06a-106">建立 BizTalk WCF 配接器。</span><span class="sxs-lookup"><span data-stu-id="aa06a-106">Create a BizTalk WCF adapter.</span></span>  
  
-   <span data-ttu-id="aa06a-107">設定 BAM WCF 攔截。</span><span class="sxs-lookup"><span data-stu-id="aa06a-107">Configure the BAM WCF interception.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aa06a-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="aa06a-108">In This Section</span></span>  
  
-   [<span data-ttu-id="aa06a-109">如何新增 BAM 攔截器行為至 Machine.config 檔案</span><span class="sxs-lookup"><span data-stu-id="aa06a-109">How to Add the BAM Interceptor Behavior to the Machine.config File</span></span>](../core/how-to-add-the-bam-interceptor-behavior-to-the-machine-config-file.md)  
  
-   [<span data-ttu-id="aa06a-110">如何建立 BizTalk Server WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="aa06a-110">How to Create a WCF Adapter for BizTalk Server</span></span>](../core/how-to-create-a-wcf-adapter-for-biztalk-server.md)  
  
-   [<span data-ttu-id="aa06a-111">如何設定接收和傳送位置以及連接埠的 BAM WCF 攔截</span><span class="sxs-lookup"><span data-stu-id="aa06a-111">How to Configure Receive and Send Locations and Ports for BAM WCF Interception</span></span>](../core/how-to-configure-receive-and-send-locations-and-ports-for-bam-wcf-interception.md)  
  
-   [<span data-ttu-id="aa06a-112">如何設定 BAM WCF 攔截</span><span class="sxs-lookup"><span data-stu-id="aa06a-112">How to Configure the BAM WCF Interception</span></span>](../core/how-to-configure-the-bam-wcf-interception.md)  
  
-   [<span data-ttu-id="aa06a-113">使用錯誤處理</span><span class="sxs-lookup"><span data-stu-id="aa06a-113">Using Fault Handling</span></span>](../core/using-fault-handling.md)