---
title: 如何擷取 BizTalk 程序的記憶體傾印 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8053fcf3-b331-4245-b3c3-21290463e0c0
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3643dab17f8d1592f1e5fddce30aa12e537c817
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969135"
---
# <a name="how-to-capture-a-memory-dump-of-a-biztalk-process"></a>如何擷取 BizTalk 程序的記憶體傾印
在特定情況下，您必須擷取執行於 BizTalk Server 之程序的記憶體傾印，以便深入分析程序。 下列情況可能必須分析記憶體傾印：  
  
- 程序無回應時。  
  
- 程序損毀時。  
  
- 程序發生記憶體溢位時。  
  
  本節包含擷取適當類型的記憶體傾印時，應該遵循的步驟。  
  
## <a name="installation-of-the-iis-diagnostics-toolkit"></a>安裝 IIS Diagnostics Toolkit  
 在本節中主題的每個需要使用**Debug Diagnostics Tool** IIS Diagnostics toolkit 來擷取記憶體傾印。 若要安裝**Debug Diagnostics Tool** IIS Diagnostics toolkit，請遵循下列步驟：  
  
1.  下載 IIS Diagnostics Toolkit，從[Internet Information Services 診斷工具](http://go.microsoft.com/fwlink/?LinkId=64426)。  
  
2.  按兩下 **[iisdiag.msi]** 來啟動 IIS Diagnostics Toolkit 安裝程式，然後選擇**自訂**安裝類型。  
  
3.  在 [**自訂安裝程式**] 對話方塊中，確定的選項**Debug Diagnostics Tool 1.0**已啟用，並完成安裝程式中的步驟。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何擷取沒有回應的處理序的記憶體傾印](../core/how-to-capture-a-memory-dump-of-a-process-that-is-non-responsive.md)  
  
-   [如何擷取損毀程序的記憶體傾印](../core/how-to-capture-a-memory-dump-of-a-process-that-is-crashing.md)  
  
-   [如何擷取發生記憶體溢位的處理序的記憶體傾印](../core/how-to-capture-a-memory-dump-of-a-process-that-is-leaking-memory.md)  
  
-   [如何使用 Debug Diagnostics 分析記憶體傾印](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)