---
title: "使用安裝指令碼的 JMS MQRFH2 範例安裝 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 785f3e32-83b4-406a-af1b-9499115fbb8f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: edb3102fabc84818cb42fcdcba6a034d085bdcc4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="install-the-jms-mqrfh2-sample-using-the-install-scripts"></a><span data-ttu-id="0fcc9-102">安裝 JMS MQRFH2 範例使用安裝指令碼</span><span class="sxs-lookup"><span data-stu-id="0fcc9-102">Install the JMS MQRFH2 Sample Using the Install Scripts</span></span>
<span data-ttu-id="0fcc9-103">本章節描述如何安裝使用所提供的安裝指令碼的 JMS MQRFH2 範例[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0fcc9-103">This section describes how you can install the JMS MQRFH2 sample using the install scripts provided with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span>  
  
 <span data-ttu-id="0fcc9-104">**若要安裝 JMS MQRFH2 範例的安裝指令碼**</span><span class="sxs-lookup"><span data-stu-id="0fcc9-104">**To install the JMS MQRFH2 samples from the install scripts**</span></span>  
  
1.  <span data-ttu-id="0fcc9-105">使用 WebSphere 總管 中，建立具有名稱的佇列管理員**ESB。JMS。Sample.QueueManager**。</span><span class="sxs-lookup"><span data-stu-id="0fcc9-105">Using WebSphere Explorer, create a Queue Manager with the name **ESB.JMS.Sample.QueueManager**.</span></span>  
  
2.  <span data-ttu-id="0fcc9-106">使用 WebSphere 總管 中，建立下列四個佇列內**ESB。JMS。Sample.QueueManager:**</span><span class="sxs-lookup"><span data-stu-id="0fcc9-106">Using WebSphere Explorer, create the following four queues within **ESB.JMS.Sample.QueueManager:**</span></span>  
  
    -   <span data-ttu-id="0fcc9-107">ESB。JMS。範例。DYNAMICQ1</span><span class="sxs-lookup"><span data-stu-id="0fcc9-107">ESB.JMS.SAMPLE.DYNAMICQ1</span></span>  
  
    -   <span data-ttu-id="0fcc9-108">ESB。JMS。範例。DYNAMICQ2</span><span class="sxs-lookup"><span data-stu-id="0fcc9-108">ESB.JMS.SAMPLE.DYNAMICQ2</span></span>  
  
    -   <span data-ttu-id="0fcc9-109">ESB。JMS。範例。回覆</span><span class="sxs-lookup"><span data-stu-id="0fcc9-109">ESB.JMS.SAMPLE.REPLY</span></span>  
  
    -   <span data-ttu-id="0fcc9-110">ESB。JMS。範例。SENDTOBIZTALK</span><span class="sxs-lookup"><span data-stu-id="0fcc9-110">ESB.JMS.SAMPLE.SENDTOBIZTALK</span></span>  
  
3.  <span data-ttu-id="0fcc9-111">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="0fcc9-111">On the **Start** menu, click **Run**.</span></span>  
  
4.  <span data-ttu-id="0fcc9-112">在**執行** 對話方塊中，輸入**cmd**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="0fcc9-112">In the **Run** dialog box, type **cmd**, and then press ENTER.</span></span>  
  
5.  <span data-ttu-id="0fcc9-113">執行下列命令，取代*\<路徑\>*參數與您想要安裝的.cmd 檔案的完整路徑 (在此版本中的預設路徑是 \Source\Samples\JMS\Install\Scripts\\):</span><span class="sxs-lookup"><span data-stu-id="0fcc9-113">Run the following command, replacing the *\<path\>* parameter with the full path to the .cmd file you want to install (the default path in this release is \Source\Samples\JMS\Install\Scripts\\):</span></span>  
  
    ```  
    <path>\Setup_bin.cmd  
    ```