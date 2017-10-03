---
title: "向上擴充 BizTalk Server 層 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, scaling
- scaling, examples
- scaling, scaling up
ms.assetid: 9002006a-f301-4e15-94b9-6caffd7c527c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d55176072cd33e20dd1024bf2d9d1c39bca4567a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scaling-up-the-biztalk-server-tier"></a>向上擴充 BizTalk Server 層
若要向上擴充 BizTalk 層，您需要升級 CPU、記憶體、IO 及其他資源。 下圖顯示如何將 BizTalk 層從擁有兩台處理器的電腦向上擴充到擁有四台處理器之電腦的範例。  
  
 ![小數位數 &#45; 向上 BTS](../core/media/scaleupbts.gif "ScaleUpBTS")  
  
 向上擴充 BizTalk 階層的實例與選擇向外擴充的時機類似：  
  
-   BizTalk Server 成為瓶頸。 瓶頸本身可能是由於以下其中一個問題所造成：  
  
-   CPU：若實例使用大量 CPU 管線、對應或協調流程，BizTalk Server 將不會有額外的 CPU 空間。  
  
-   記憶體和 I/O：若是現有電腦的記憶體與 IO 已達到最大限制，則需要升級電腦。  
  
-   向外擴充過於昂貴。  
  
-   若向外擴充並未解決瓶頸。 例如，向外擴充不會解決下列瓶頸：  
  
    -   大型訊息轉換  
  
    -   每個交換都有大量訊息  
  
    -   有些 BTS 元件 (如管線或配接器) 會耗用大量記憶體  
  
    -   傳輸，如 EDI  
  
## <a name="when-you-cant-scale-up-the-biztalk-tier"></a>無法向上擴充 BizTalk 層時  
  
-   MessageBox 資料庫成為瓶頸。  
  
-   配接器成為瓶頸。 比方說，如果您使用配接器之後您增加 BizTalk 接收器的數目,，則可能會增加鎖定爭用其中 BizTalk 配接器從中提取資料的後端應用程式上。 這樣會限制您向上擴充配接器的能力。  
  
## <a name="see-also"></a>另請參閱  
 [向外擴充 BizTalk Server 層](../core/scaling-out-the-biztalk-server-tier.md)   
 [向上擴充 SQL Server 層](../core/scaling-up-the-sql-server-tier.md)   
 [向外擴充 SQL Server 層](../core/scaling-out-the-sql-server-tier.md)   
 [向外擴充接收主控件](../core/scaled-out-receiving-hosts.md)   
 [向外延展處理主控件](../core/scaled-out-processing-hosts.md)   
 [向外延展傳送主控件](../core/scaled-out-sending-hosts.md)   
 [使用 Windows 伺服器叢集以提供高可用性的 BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)   
 [向外延展資料庫](../core/scaled-out-databases.md)   
 [叢集 BizTalk Server 資料庫](../core/clustering-the-biztalk-server-databases1.md)