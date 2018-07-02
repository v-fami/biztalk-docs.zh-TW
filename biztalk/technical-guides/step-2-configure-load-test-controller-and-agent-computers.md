---
title: 步驟 2： 設定負載測試控制器和代理程式電腦 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e9d937ac-55d8-48fa-bba2-3efe151587b8
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b03a191269936311d04f7b773ed3159db66e34f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972447"
---
# <a name="step-2-configure-load-test-controller-and-agent-computers"></a>步驟 2： 設定負載測試控制器和代理程式電腦

## <a name="overview"></a>概觀
Visual Studio 可以產生模擬最多 250 個虛擬使用者，在本機的負載測試回合的負載。 若要模擬超過 250 位虛擬使用者和/或測試從遠端電腦需要有 Visual Studio 負載測試虛擬使用者。  
  
 所有負載測試執行本指南中，是從兩台電腦都起始：  
  
- 為負載測試控制器和負載測試代理程式執行的一部電腦。  
  
- 執行負載測試代理程式只為另一部電腦。  
  
  測試結果已儲存在遠端負載測試結果儲存機制中的 SQL Server 資料庫。  
  
  如需使用 負載測試分散到多部測試電腦的 測試控制器和測試代理程式的詳細資訊，請參閱[散發負載測試跨多部測試機器使用測試控制器和測試代理程式](https://msdn.microsoft.com/library/dd728093.aspx)。  
  
## <a name="install-and-configure-the-load-test-controller-and-load-test-agents"></a>安裝和設定負載測試控制器和負載測試代理程式  
 若要安裝並設定負載測試控制器，負載測試代理程式，請參閱[安裝和設定測試代理程式](https://docs.microsoft.com/visualstudio/test/lab-management/install-configure-test-agents)。
