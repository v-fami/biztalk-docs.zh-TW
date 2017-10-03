---
title: "如何使用 BAM 管理公用程式的 BAM 資料庫的設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 801338f4-b363-4f8e-b248-9c628065ded2
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9343cf9bd33f5880c564e2ec0dce72ece520ff01
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-up-the-bam-databases-using-the-bam-management-utility"></a>如何使用 BAM 管理公用程式安裝 BAM 資料庫
一般而言，系統管理員會使用 BizTalk Server 組態公用程式安裝 BAM 資料庫。 您可以用另一種方法，也就是使用 BAM 管理公用程式 (bm.exe) 來安裝資料庫。  
  
## <a name="prerequisites"></a>必要條件  
 以下是執行此主題中之程序的必要條件：  
  
-   您必須擁有裝載 BAMPrimaryImport、BAMStarSchema 和 BAMArchive 資料庫之 SQL 伺服器的系統管理員權限。  
  
-   若要安裝 SQL Notification Services 資料庫，您必須擁有系統管理員權限，並且隸屬於本機系統管理員群組及任何其他已設定的系統管理員群組 (例如 BTS Admins 群組)。  
  
-   您必須擁有包含 XML 資料的 BAM 組態檔案，以便用來安裝建立資料庫。  
  
### <a name="to-set-up-the-bam-databases-using-the-bam-management-utility"></a>使用 BAM 管理公用程式安裝 BAM 資料庫  
  
1.  開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2.  瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。  
  
3.  在命令提示字元輸入下列命令： **bm 安裝程式資料庫 ConfigFile:\<組態檔 >**，其中\<*組態檔*> 取代為的名稱您的 BAM 組態檔。 按 ENTER 鍵。  
  
## <a name="see-also"></a>另請參閱  
 [BAM 管理公用程式](../core/bam-management-utility.md)