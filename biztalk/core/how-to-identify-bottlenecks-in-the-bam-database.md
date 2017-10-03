---
title: "如何識別 BAM 資料庫中的瓶頸 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6814c0df-3ce1-44f8-8e63-af6e23336c6d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8fa54379d6d314993ac33b7d6395f061e48849d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-identify-bottlenecks-in-the-bam-database"></a><span data-ttu-id="c3b65-102">如何識別 BAM 資料庫中的瓶頸</span><span class="sxs-lookup"><span data-stu-id="c3b65-102">How to Identify Bottlenecks in the BAM Database</span></span>
<span data-ttu-id="c3b65-103">若要識別 BAM 資料庫中的瓶頸，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="c3b65-103">To identify bottlenecks in the BAM database, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="c3b65-104">確定作用中執行個體的計數未上升。</span><span class="sxs-lookup"><span data-stu-id="c3b65-104">Ensure that the Active Instances count is not climbing.</span></span>  
  
2.  <span data-ttu-id="c3b65-105">確認 SQL-Agent 服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="c3b65-105">Ensure that the SQL-Agent Service is running.</span></span>  
  
3.  <span data-ttu-id="c3b65-106">如果已設定 OLAP 分析，請確定 BAM_AN_ job 以定期間隔執行。</span><span class="sxs-lookup"><span data-stu-id="c3b65-106">If OLAP Analysis is configured ensure that the BAM_AN_ job is running at periodic intervals.</span></span>  
  
4.  <span data-ttu-id="c3b65-107">確定 BAM_DM_ (Data Maintenance) 工作排定為以定期間隔執行。</span><span class="sxs-lookup"><span data-stu-id="c3b65-107">Ensure that BAM_DM_ (Data Maintenance) job is scheduled to run at periodic intervals.</span></span>