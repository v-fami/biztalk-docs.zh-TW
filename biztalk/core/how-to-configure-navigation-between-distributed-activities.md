---
title: "How to Configure 之間瀏覽分散式活動 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f8faf0a-eb06-4383-932d-4106306d6cf3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ab210f5ab728134b406b5c4bdaf25a1ec6db1c2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-navigation-between-distributed-activities"></a>如何設定分散式活動之間的導覽
分散式導覽讓使用者得以檢視現存於遠端 BAM 部署中的活動。 啟用分散式導覽後，任一部電腦上 BAM 入口網站的使用者都可以檢視其他 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署中 BAM 入口網站上的活動。  
  
 本主題中的程序舉下列實例說明如何啟用分散式導覽：  
  
-   業務部門由 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署在電腦 1。  
  
-   貨運部門由 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署在電腦 2。  
  
-   myBusinessView 檢視連同稱為「銷售資料」的活動部署在電腦 1。  
  
-   myBusinessView 檢視連同稱為「送貨資料」的活動安裝在電腦 2。  
  
-   業務部門的商務使用者基於商務需求而同時查看兩部電腦上的活動。  
  
### <a name="how-to-set-up-distributed-navigation-for-remote-activities"></a>如何為遠端活動設定分散式導覽  
  
1.  電腦 1 的系統管理員授與商務使用者存取電腦 1 上的 myBusinessView 檢視。 使用 bm.exe 命令，如下：**新增帳戶-AccountName:\<帳戶名稱\>-檢視：** myBusinessView  
  
2.  電腦 1 上的系統管理員，如下所示執行啟用參考命令，來啟用分散式的導覽： **bm.exe 啟用參考 TargetServer:** computer2 **-TargetDatabase:\<目標資料庫\>**  
  
    > [!NOTE]
    >  一般來說，跨部門從不同的電腦存取 BAM Web 服務時所用的帳戶會各有不同。 因此，在此案例中電腦 1 的系統管理員必須加入 Web 服務模擬帳戶，電腦 1 的電腦 2 的 BAM 主要匯入資料庫的 BAM_ManagementWS 角色。 詳細資訊，請參閱 「 檢視和修改角色成員資格 >，網址[http://go.microsoft.com/fwlink/?LinkId=66990](http://go.microsoft.com/fwlink/?LinkId=66990)。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
3.  電腦 2 的系統管理員使用步驟 1 提到的 BM.exe 命令，授與商務使用者存取電腦 2 上的 myBusinessView 檢視。  
  
## <a name="results-of-setting-up-distributed-navigation"></a>設定分散式導覽的結果  
 啟用分散式導覽後，已獲授權存取這兩部電腦上指定檢視的使用者將可在其主要入口網站的 [我的檢視] 窗格中，看到部署在這些電腦上之指定檢視的相關活動。 當這些使用者會按一下裝載於遠端部署的活動時，會順暢地導向至入口網站上的活動裝載，並能夠檢視的活動，就好像在其預設入口網站上。  
  
> [!NOTE]
>  您可以雙向啟用分散式導覽。 若同時在共用遠端活動的兩部電腦上執行上述程序，則任一電腦之入口網站的商務使用者皆可使用分散式導覽。  
  
## <a name="see-also"></a>請參閱  
 [管理遠端活動的分散式的導覽](../core/managing-distributed-navigation-of-remote-activities.md)   
 [BAM 入口網站](../core/bam-portal.md)