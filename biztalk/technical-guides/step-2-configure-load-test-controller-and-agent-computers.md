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
ms.openlocfilehash: 0f931a05796856816e19b53ff5cba9f53b48c3e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-load-test-controller-and-agent-computers"></a>步驟 2： 設定負載測試控制器和代理程式的電腦
Visual Studio 2010 Ultimate 版可能會產生模擬本機負載測試回合上的最多 250 個虛擬使用者負載。 若要模擬超過 250 位虛擬使用者和/或起始測試從遠端電腦需要有 Visual Studio 負載測試虛擬使用者組件 2010年。  
  
 所有負載測試執行本指南是從兩台電腦都起始：  
  
-   為負載測試控制器和負載測試代理程式執行的一部電腦。  
  
-   執行負載測試代理程式只能以另一部電腦。  
  
 測試結果儲存在遠端的負載測試結果儲存機制中的 SQL Server 2008 R2 資料庫。  
  
 如需可以分散多部測試電腦上的負載測試中使用測試控制器和測試代理程式的詳細資訊，請參閱[散發負載測試跨多個測試機器使用測試控制器和測試代理程式](http://go.microsoft.com/fwlink/?LinkId=208406)(http://go.microsoft.com/fwlink/ 嗎？LinkId = 208406)。  
  
## <a name="install-and-configure-the-load-test-controller-and-load-test-agents"></a>安裝和設定負載測試控制器和負載測試代理程式  
 若要安裝和設定負載測試控制器和負載測試代理程式，請參閱本主題中的下列章節[安裝和設定 Visual Studio Agents 和測試和組建控制器](http://go.microsoft.com/fwlink/?LinkId=208455)(http://go.microsoft.com/fwlink/?LinkId=208455):  
  
-   若要安裝測試控制器，請依照中的程序[安裝測試控制器](http://go.microsoft.com/fwlink/?LinkId=208454)(http://go.microsoft.com/fwlink/?LinkId=208454) 一節。  
  
-   若要安裝測試代理程式，請依照中的程序[安裝測試代理程式](http://go.microsoft.com/fwlink/?LinkId=208456)(http://go.microsoft.com/fwlink/?LinkId=208456) 一節。