---
title: "步驟 2： 設定負載測試控制器和代理程式電腦 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9d937ac-55d8-48fa-bba2-3efe151587b8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75a659d533b68cf525bcd782a2dadce72a6ebb0b
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="step-2-configure-load-test-controller-and-agent-computers"></a>步驟 2： 設定負載測試控制器和代理程式的電腦

## <a name="overview"></a>概觀
Visual Studio 可能會產生模擬本機負載測試回合上的最多 250 個虛擬使用者負載。 若要模擬超過 250 位虛擬使用者和/或起始測試從遠端電腦需要有 Visual Studio 負載測試虛擬使用者。  
  
 所有負載測試執行本指南是從兩台電腦都起始：  
  
-   為負載測試控制器和負載測試代理程式執行的一部電腦。  
  
-   執行負載測試代理程式只能以另一部電腦。  
  
 測試結果儲存在遠端的負載測試結果儲存機制中的 SQL Server 資料庫中。  
  
 如需可以分散多部測試電腦上的負載測試中使用測試控制器和測試代理程式的詳細資訊，請參閱[散發負載測試跨多個測試機器使用測試控制器和測試代理程式](https://msdn.microsoft.com/library/dd728093.aspx)。  
  
## <a name="install-and-configure-the-load-test-controller-and-load-test-agents"></a>安裝和設定負載測試控制器和負載測試代理程式  
 若要安裝和設定負載測試控制器和負載測試代理程式，請參閱[安裝和設定測試代理程式](https://docs.microsoft.com/visualstudio/test/lab-management/install-configure-test-agents)。
