---
title: 設定時區和 BizTalk Server 中的循環排程 |Microsoft 文件
ms.custom: ''
ms.date: 11/20/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d60ae7be-747e-4034-8b99-46bd7e25fe67
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ab4cd85af0d15d7b089b106dc33aa77f1a10639
ms.sourcegitcommit: f65e8ed2b8c18cded26b9d60868fb6a56bcc1205
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
ms.locfileid: "25497767"
---
# <a name="configure-the-time-zone-and-recurrence-scheduling-in-biztalk-server"></a>設定時區和 BizTalk Server 中的循環排程
設定時區，並設定週期性排程上您在中接收位置[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。 

**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，進階排程功能在接收位置包含一些選項。 使用進階排程選項，設定時區，並且也設定了循環排程。

本主題會示範如何設定這些功能。

## <a name="prerequisites"></a>必要條件
安裝[功能套件 2](https://aka.ms/bts2016fp2)上您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。

## <a name="time-zone"></a>時區

**排程**接收位置的屬性包括**時區**屬性。 設定時，您在接收位置中選擇的時區為準而不是本機電腦上的時區。 

所有日期和時間在**排程**屬性專屬於您所選擇的時區。 任何現有的排程會移轉裝載 BizTalk 管理資料庫 (BizTalkMgmtDb) 的伺服器的時區。 

您也可以調整日光節約時間 (DST)。 有選取時，排程會自動調整您選擇的時區的日光節約時間。 如果此選項的排程上沒有任何影響：

* 指定的時區並沒有日光節約時間
* 您選擇的時區中未觀察到日光節約時間

## <a name="enable-recurrence-schedule"></a>啟用循環排程
1. 在**BizTalk Server 管理**主控台中，以滑鼠右鍵按一下其中一個您接收位置，然後選取**屬性**。 
2. 在**排程**頁面上，選取**啟用服務窗口**。 **開始時間**和**停止時間**設定排程，才能執行的初始時間：

    ![啟用服務視窗的接收埠](../core/media/enable-service-windows-for-receive-port.PNG)

3. 會顯示其他排程選項：

    ![進階排程的接收埠](../core/media/advanced-scheduling-for-receive-port.PNG)

4. **循環**屬性執行每日、 週或月您所選擇的接收埠： 

    1. 使用**每日**循環執行的接收埠每*x*天，開始的數字**從**日期選擇，並只在**服務窗口**您選擇：

        ![每日排程](../core/media/daily-shcedule.png)

    2. 使用**每週**循環執行的接收埠的特定日期一週內，並只在**服務窗口**您選擇： 

        ![每週排程](../core/media/weekly-shcedule.png)

    3. 使用**每月**每月排程執行的接收埠的循環。 **天**和**上**可用選項。 
    
        使用**天**循環週期內的特定日期上執行的接收埠**月**您選擇： 

        ![每月排程](../core/media/monthly-shcedule.PNG)

        使用**上**上執行的接收埠上一個月中特定日的循環：

        ![每月排程上](../core/media/monthly-on-shcedule.PNG)

5. 選取 [確定] 儲存您的變更。 

## <a name="see-also"></a>另請參閱
[設定此功能套件](../core/configure-the-feature-pack.md)