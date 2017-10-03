---
title: "如何識別 BizTalkDTADb 資料庫中的瓶頸 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4499bc3-d50b-4b97-b19c-93c7bcc40483
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c7463a0288733936189d3cbbb69b59b3b202419
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-identify-bottlenecks-in-the-biztalkdtadb-database"></a><span data-ttu-id="05ec5-102">如何識別 BizTalkDTADb 資料庫中的瓶頸</span><span class="sxs-lookup"><span data-stu-id="05ec5-102">How to Identify Bottlenecks in the BizTalkDTADb Database</span></span>
<span data-ttu-id="05ec5-103">若要找出 BizTalkDTADb 資料庫中的瓶頸，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="05ec5-103">To identify bottlenecks in the BizTalkDTADb database, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="05ec5-104">確認 SQL-Agent 服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="05ec5-104">Ensure that the SQL-Agent Service is running.</span></span>  
  
2.  <span data-ttu-id="05ec5-105">確定「封存/清除作業」服務正在執行而且即將順利完成。</span><span class="sxs-lookup"><span data-stu-id="05ec5-105">Ensure that the Archive/Purge Job is running and completing successfully.</span></span>  
  
3.  <span data-ttu-id="05ec5-106">確認是否有足夠的可用磁碟空間可以容納 DTADb 封存和資料庫成長。</span><span class="sxs-lookup"><span data-stu-id="05ec5-106">Verify that sufficient free disk space is available for the DTADb archives and database growth.</span></span>