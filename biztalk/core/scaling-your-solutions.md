---
title: "擴充您的解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, scaling
- scaling, scaling out
- scaling, performance
- scaling, about scaling
- scaling, scaling up
- scaling
ms.assetid: e2acbaa4-29d3-4c89-ac1f-c0641cfa0442
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5417e303ea8486ef5bdee8e57c66d4783fb197ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scaling-your-solutions"></a>擴充您的解決方案
BizTalk Server 架構針對擴充性提供非常良好的支援。 您所選擇的擴充模式，則會根據實例的複雜度、硬體，以及輸送量/延遲需求而定。 您應該從較小的拓樸開始，然後根據本節的指導方針嘗試擴充或縮小。  
  
## <a name="scaling-out-and-scaling-up"></a>向外擴充和向上擴充  
 有兩種方式可以擴充您的 BizTalk Server 系統：  
  
-   向外擴充是新增其他電腦的程序。 例如，若 BizTalk Server 的瓶頸是來自 CPU 資源，則新增其他伺服器可提供雙倍的 CPU 資源，進而提供雙倍的輸送量。  
  
-   向上擴充是升級現有電腦的程序。 例如，您可以將 BizTalk Server 電腦從擁有四個處理器的電腦升級為擁有八個處理器的電腦。  
  
 BizTalk Server 系統有兩層：BizTalk Server 層，以及包含 MessageBox 資料庫的 SQL Server 層。 在任何實例中，您都可以向外擴充或向上擴充每一層。 也就是說，您可以向外擴充 BizTalk Server 和 MessageBox 資料庫，或是向上擴充這兩者。  
  
 在大部分情況下，BizTalk 層會先成為瓶頸，而您可以使其向外擴充以便開始改善效能。不過，在某個時點，視您所使用的系統和硬體複雜度而定，您將無法繼續向外擴充 BizTalk 層，而 SQL Server 層會變成瓶頸。 接著，您可以向上擴充 SQL Server 層，然後新增更多 MessageBox 資料庫來使其向外擴充。  
  
> [!NOTE]
>  在此處，新的 MessageBox 資料庫不一定代表有其他伺服器。 單一 SQL 伺服器可以有多個 MessageBox 資料庫。 此外，若資料庫位於不同的電腦上，多個 MessageBox 資料庫會產生 DTC 成本和網路躍點。  
  
 理論上，只要主要 MessageBox 資料庫尚未飽和，SQL Server 層就可以無限向外擴充。  
  
 本節中的主題會更詳細地描述這些擴充模式。 這些主題也會說明如何擴充每個模式，以及如何判定您何時無法再使用該模式來擴充系統。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [什麼是擴充性？](../core/what-is-scalability.md)  
  
-   [向外擴充 BizTalk Server 層](../core/scaling-out-the-biztalk-server-tier.md)  
  
-   [向上擴充 BizTalk Server 層](../core/scaling-up-the-biztalk-server-tier.md)  
  
-   [向外擴充 SQL Server 層](../core/scaling-out-the-sql-server-tier.md)  
  
-   [向上擴充 SQL Server 層](../core/scaling-up-the-sql-server-tier.md)  
  
## <a name="see-also"></a>另請參閱  
 [向外擴充接收主控件](../core/scaled-out-receiving-hosts.md)   
 [向外延展處理主控件](../core/scaled-out-processing-hosts.md)   
 [向外延展傳送主控件](../core/scaled-out-sending-hosts.md)   
 [使用 Windows 伺服器叢集以提供高可用性的 BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)   
 [向外延展資料庫](../core/scaled-out-databases.md)   
 [叢集 BizTalk Server 資料庫](../core/clustering-the-biztalk-server-databases1.md)