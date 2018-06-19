---
title: 如何開發具有相依性的協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5464096e-66d8-48de-bc02-c754c5cfbada
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93f8d086a60487e144b02c01a393eb6f10a63b40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249478"
---
# <a name="how-to-develop-interdependent-orchestrations"></a>如何開發具有相依性的協調流程
您可以使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 開發一組具有相依性 Web 服務的協調流程。 當第一個協調流程呼叫第二個協調流程，而且第二個協調流程參考第一個協調流程中的資料型別和 (或) 連接埠時，會發生這種情況。 這種實例的範例有下列特性：  
  
-   您有兩個以上的協調流程。  
  
-   第一個協調流程 (Orch1) 透過單向 Web 服務呼叫來呼叫第二個協調流程 (Orch2)。  
  
-   Orch2 透過 Web 服務呼叫來回應 Orch1。  
  
 此專案類型的一個範例，請參閱[教學課程 2： 訂單程序](http://msdn.microsoft.com/library/a324ef1b-39b3-49ab-9719-a13f526cb467)。  
  
### <a name="to-develop-two-interdependent-orchestrations-orch1-and-orch2"></a>若要開發兩個具有相依性的協調流程 Orch1 和 Orch2  
  
1.  使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，建立其接收埠將公開為 Web 服務的 Orch1 部分版本。  
  
2.  編譯 Orch1。  
  
3.  執行 [Web 服務發佈精靈] 並發佈此連接埠。  
  
4.  使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，建立並完成 Orch2，其取用 Orch1 的 Web 服務。  
  
5.  編譯 Orch2。  
  
6.  執行 [Web 服務發佈精靈] 並發佈連接埠。  
  
7.  完成 Orch1，並在必要時取用 Orch2 的 Web 服務。  
  
8.  重新編譯 Orch1。  
  
9. 部署 Orch1 和 Orch2。  
  
## <a name="see-also"></a>另請參閱  
 [如何使用 BizTalk Web 服務發佈精靈發佈為 Web 服務的協調流程](../core/publish-orchestration-as-web-service--biztalk-web-services-publishing-wizard.md)