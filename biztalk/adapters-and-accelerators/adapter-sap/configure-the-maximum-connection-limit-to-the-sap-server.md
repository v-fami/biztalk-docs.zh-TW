---
title: 設定 SAP 伺服器的最大連接限制 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 858ed90e-b219-43cc-ad63-ae8e1eb2159a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 853a3b78b82e242750e30099f847045ff590f125
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215846"
---
# <a name="configure-the-maximum-connection-limit-to-the-sap-server"></a><span data-ttu-id="c0b57-102">設定 SAP 伺服器的最大連接限制</span><span class="sxs-lookup"><span data-stu-id="c0b57-102">Configure the Maximum Connection Limit to the SAP Server</span></span>
<span data-ttu-id="c0b57-103">適用於 SAP 資料提供者可讓配接器用戶端控制，可以在內部開啟提供者的連接數目上限。</span><span class="sxs-lookup"><span data-stu-id="c0b57-103">The Data Provider for SAP enables adapter clients to control the maximum number of connections that can be opened by the provider internally.</span></span> <span data-ttu-id="c0b57-104">您可以設定環境變數，CPIC_MAX_CONV 來控制。</span><span class="sxs-lookup"><span data-stu-id="c0b57-104">You can control this by setting the environment variable, CPIC_MAX_CONV.</span></span>  
  
 <span data-ttu-id="c0b57-105">比方說，如果 CPIC_MAX_CONV 設為任何數值，隨時開啟的 RFC 連線的數目將小於或等於該數值。</span><span class="sxs-lookup"><span data-stu-id="c0b57-105">For example, if CPIC_MAX_CONV is set to any numerical value, the number of RFC connections opened at any time will be less than or equal to that numerical value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0b57-106">數值會套用的每個個別下程序/appdomain 來設定此值。</span><span class="sxs-lookup"><span data-stu-id="c0b57-106">The numerical value will be applicable for every server individually under the process/appdomain which sets this value.</span></span>  
  
 <span data-ttu-id="c0b57-107">比方說，如果應用程式中使用 Data provider for SAP，已在"x"的處理序層級上設定其環境變數，並連接到兩個不同的伺服器 A 和 B，然後最大數目的同時連線 A 和 B 會是"x"分別。</span><span class="sxs-lookup"><span data-stu-id="c0b57-107">For example, if an application using Data provider for SAP, has set its environment variable at process level to “x” and connects to two different servers A and B, then the maximum number of connections for both A and B will be “x” respectively.</span></span>