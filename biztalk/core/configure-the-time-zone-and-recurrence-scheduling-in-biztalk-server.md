---
title: 設定時區與週期排程在 BizTalk Server |Microsoft Docs
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
ms.openlocfilehash: fe12e4fe81705d178520f02591f8179e47606f6c
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50753288"
---
# <a name="configure-the-time-zone-and-recurrence-scheduling-in-biztalk-server"></a>設定時區與週期排程在 BizTalk Server
設定時區和週期性排程進行您在中接收位置[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。 

**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，排程的進階的功能，在接收位置包含了一些選項。 使用進階排程選項，設定時區，並也設定週期性排程。

本主題說明如何設定這些功能。

## <a name="prerequisites"></a>先決條件
安裝[Feature Pack 2](https://aka.ms/bts2016fp2)在您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。

## <a name="time-zone"></a>時區

**排程**接收位置的屬性包括**時區**屬性。 設定時，您選擇在接收位置的時區使用而不是本機電腦上的時區。 

所有日期和時間**排程**屬性專屬於您所選擇的時區。 任何現有的排程會移轉至裝載 BizTalk 管理資料庫 (BizTalkMgmtDb) 的伺服器的時區。 

您也可以調整日光節約時間 (DST)。 有選取時，排程自動調整，以您選擇的時區的日光節約時間。 如果此選項沒有任何影響排程上：

* 指定的時區與日光節約時間沒有
* 日光節約時間未觀察到在您選擇的時區

## <a name="enable-recurrence-schedule"></a>啟用循環排程
1. 在 [ **BizTalk Server 管理]** 主控台中，以滑鼠右鍵按一下其中一個您接收位置，然後選取**屬性**。 
2. 在 **排程**頁面上，選取**啟用服務窗口**。 **開始時間**並**停止時間**設定允許的排程執行的初始時間：

    ![啟用服務 Windows 的接收埠](../core/media/enable-service-windows-for-receive-port.PNG)

3. 會顯示其他的排程選項：

    ![進階排程的接收埠](../core/media/advanced-scheduling-for-receive-port.PNG)

4. **循環**屬性執行每日、 週或月您所選擇的接收埠： 

    1. 使用**每日**循環，若要執行的接收埠每*x*天，起**從**您所選擇的日期，只有在**服務窗口**您選擇：

        ![每日排程](../core/media/daily-schedule.png)

    2. 使用**每週**上特定一天一週內，並只有在執行的接收埠的循環**服務窗口**您選擇： 

        ![每週排程](../core/media/weekly-schedule.png)

    3. 使用**每月**每月的排程執行的接收埠的循環。 **天**並**上**選項可用。 
    
        使用**天**內的特定日期上執行的接收埠的循環**月份**您選擇： 

        ![每月排程](../core/media/monthly-schedule.PNG)

        使用**上**循環，若要在當月的特定幾天執行的接收埠：

        ![每月在排程上](../core/media/monthly-on-schedule.PNG)

5. 選取 [確定] 儲存您的變更。 

## <a name="see-also"></a>另請參閱
[設定 Feature Pack](../core/configure-the-feature-pack.md)
