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
# <a name="configure-the-time-zone-and-recurrence-scheduling-in-biztalk-server"></a><span data-ttu-id="31073-102">設定時區與週期排程在 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="31073-102">Configure the time zone and recurrence scheduling in BizTalk Server</span></span>
<span data-ttu-id="31073-103">設定時區和週期性排程進行您在中接收位置[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="31073-103">Set the timezone and configure a recurrence schedule on your receive locations in [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> 

<span data-ttu-id="31073-104">**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** ，排程的進階的功能，在接收位置包含了一些選項。</span><span class="sxs-lookup"><span data-stu-id="31073-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, the advanced scheduling feature on receive locations includes some options.</span></span> <span data-ttu-id="31073-105">使用進階排程選項，設定時區，並也設定週期性排程。</span><span class="sxs-lookup"><span data-stu-id="31073-105">Using the advanced scheduling options, set the time zone, and also set a recurrence schedule.</span></span>

<span data-ttu-id="31073-106">本主題說明如何設定這些功能。</span><span class="sxs-lookup"><span data-stu-id="31073-106">This topic shows you how to configure these features.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="31073-107">先決條件</span><span class="sxs-lookup"><span data-stu-id="31073-107">Prerequisites</span></span>
<span data-ttu-id="31073-108">安裝[Feature Pack 2](https://aka.ms/bts2016fp2)在您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="31073-108">Install [Feature Pack 2](https://aka.ms/bts2016fp2) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span>

## <a name="time-zone"></a><span data-ttu-id="31073-109">時區</span><span class="sxs-lookup"><span data-stu-id="31073-109">Time zone</span></span>

<span data-ttu-id="31073-110">**排程**接收位置的屬性包括**時區**屬性。</span><span class="sxs-lookup"><span data-stu-id="31073-110">The **Schedule** properties of a receive location includes a **Time Zone** property.</span></span> <span data-ttu-id="31073-111">設定時，您選擇在接收位置的時區使用而不是本機電腦上的時區。</span><span class="sxs-lookup"><span data-stu-id="31073-111">When set, the time zone you choose in the receive location is used instead of the time zone on the local computer.</span></span> 

<span data-ttu-id="31073-112">所有日期和時間**排程**屬性專屬於您所選擇的時區。</span><span class="sxs-lookup"><span data-stu-id="31073-112">All dates and times in the **Schedule** properties are specific to the time zone you choose.</span></span> <span data-ttu-id="31073-113">任何現有的排程會移轉至裝載 BizTalk 管理資料庫 (BizTalkMgmtDb) 的伺服器的時區。</span><span class="sxs-lookup"><span data-stu-id="31073-113">Any existing schedules are migrated to the time zone of the server hosting the BizTalk Management database (BizTalkMgmtDb).</span></span> 

<span data-ttu-id="31073-114">您也可以調整日光節約時間 (DST)。</span><span class="sxs-lookup"><span data-stu-id="31073-114">You can also adjust for daylight saving time (DST).</span></span> <span data-ttu-id="31073-115">有選取時，排程自動調整，以您選擇的時區的日光節約時間。</span><span class="sxs-lookup"><span data-stu-id="31073-115">When checked, the schedule automatically adjusts to the daylight saving time of the time zone you choose.</span></span> <span data-ttu-id="31073-116">如果此選項沒有任何影響排程上：</span><span class="sxs-lookup"><span data-stu-id="31073-116">This option has no impact on the schedule if:</span></span>

* <span data-ttu-id="31073-117">指定的時區與日光節約時間沒有</span><span class="sxs-lookup"><span data-stu-id="31073-117">The specified time zone does not have a daylight saving time</span></span>
* <span data-ttu-id="31073-118">日光節約時間未觀察到在您選擇的時區</span><span class="sxs-lookup"><span data-stu-id="31073-118">Daylight saving time is not observed in the time zone you choose</span></span>

## <a name="enable-recurrence-schedule"></a><span data-ttu-id="31073-119">啟用循環排程</span><span class="sxs-lookup"><span data-stu-id="31073-119">Enable recurrence schedule</span></span>
1. <span data-ttu-id="31073-120">在 [ **BizTalk Server 管理]** 主控台中，以滑鼠右鍵按一下其中一個您接收位置，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="31073-120">In the **BizTalk Server Administration** console, right-click one of your receive locations, and select **Properties**.</span></span> 
2. <span data-ttu-id="31073-121">在 **排程**頁面上，選取**啟用服務窗口**。</span><span class="sxs-lookup"><span data-stu-id="31073-121">On the **Scheduling** page, select **Enable service window**.</span></span> <span data-ttu-id="31073-122">**開始時間**並**停止時間**設定允許的排程執行的初始時間：</span><span class="sxs-lookup"><span data-stu-id="31073-122">The **Start Time** and **Stop time** set the initial time the schedule is allowed to run:</span></span>

    ![啟用服務 Windows 的接收埠](../core/media/enable-service-windows-for-receive-port.PNG)

3. <span data-ttu-id="31073-124">會顯示其他的排程選項：</span><span class="sxs-lookup"><span data-stu-id="31073-124">The additional scheduling options are displayed:</span></span>

    ![進階排程的接收埠](../core/media/advanced-scheduling-for-receive-port.PNG)

4. <span data-ttu-id="31073-126">**循環**屬性執行每日、 週或月您所選擇的接收埠：</span><span class="sxs-lookup"><span data-stu-id="31073-126">The **Recurrence** property runs the receive port every day, week, or month that you choose:</span></span> 

    1. <span data-ttu-id="31073-127">使用**每日**循環，若要執行的接收埠每*x*天，起**從**您所選擇的日期，只有在**服務窗口**您選擇：</span><span class="sxs-lookup"><span data-stu-id="31073-127">Use the **Daily** recurrence to run the receive port every *x* number of days, starting on the **From** date you choose, and only within the **service window** you choose:</span></span>

        ![每日排程](../core/media/daily-schedule.png)

    2. <span data-ttu-id="31073-129">使用**每週**上特定一天一週內，並只有在執行的接收埠的循環**服務窗口**您選擇：</span><span class="sxs-lookup"><span data-stu-id="31073-129">Use the **Weekly** recurrence to run the receive port on a specific day within a week, and only within the **service window** you choose:</span></span> 

        ![每週排程](../core/media/weekly-schedule.png)

    3. <span data-ttu-id="31073-131">使用**每月**每月的排程執行的接收埠的循環。</span><span class="sxs-lookup"><span data-stu-id="31073-131">Use the **Monthly** recurrence to run the receive port on a monthly schedule.</span></span> <span data-ttu-id="31073-132">**天**並**上**選項可用。</span><span class="sxs-lookup"><span data-stu-id="31073-132">The **Days** and **On** options are available.</span></span> 
    
        <span data-ttu-id="31073-133">使用**天**內的特定日期上執行的接收埠的循環**月份**您選擇：</span><span class="sxs-lookup"><span data-stu-id="31073-133">Use the **Days** recurrence to run the receive port on specific dates within the **months** you choose:</span></span> 

        ![每月排程](../core/media/monthly-schedule.PNG)

        <span data-ttu-id="31073-135">使用**上**循環，若要在當月的特定幾天執行的接收埠：</span><span class="sxs-lookup"><span data-stu-id="31073-135">Use the **On** recurrence to run the receive port on specific days of the month:</span></span>

        ![每月在排程上](../core/media/monthly-on-schedule.PNG)

5. <span data-ttu-id="31073-137">選取 [確定] 儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="31073-137">Select **OK** to save your changes.</span></span> 

## <a name="see-also"></a><span data-ttu-id="31073-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31073-138">See also</span></span>
[<span data-ttu-id="31073-139">設定 Feature Pack</span><span class="sxs-lookup"><span data-stu-id="31073-139">Configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)
