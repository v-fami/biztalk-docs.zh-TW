---
title: 可以修改改善網路效能的設定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb6aacc3-e697-4cc9-b937-73a2f54e733b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8557c8bbe8c0b1c785d6da8d87e8950d3779b8d0
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="settings-that-can-be-modified-to-improve-network-performance"></a><span data-ttu-id="a6c81-102">您可以修改改善網路效能的設定</span><span class="sxs-lookup"><span data-stu-id="a6c81-102">Settings that can be Modified to Improve Network Performance</span></span>
<span data-ttu-id="a6c81-103">本主題會提供影響網路效能的建議值的描述。</span><span class="sxs-lookup"><span data-stu-id="a6c81-103">This topic provides a description of recommended values   that impact network performance.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a6c81-104">在完成本指南中的效能測試它觀察到，Windows Server 2008，會顯示預設微調。</span><span class="sxs-lookup"><span data-stu-id="a6c81-104">During performance testing completed for this guide it was observed that Windows Server 2008 appears to be tuned by default.</span></span> <span data-ttu-id="a6c81-105">對系統影響仔細分析之後，應該只有在執行修改的登錄設定。</span><span class="sxs-lookup"><span data-stu-id="a6c81-105">Modification of  registry settings should only be done after a careful analysis of the effects on the system.</span></span>  
  
## <a name="adjust-the-maxuserport-and-tcptimedwaitdelay-settings"></a><span data-ttu-id="a6c81-106">調整 MaxUserPort 和 TcpTimedWaitDelay 設定</span><span class="sxs-lookup"><span data-stu-id="a6c81-106">Adjust the MaxUserPort and TcpTimedWaitDelay settings</span></span>  
 <span data-ttu-id="a6c81-107">**MaxUserPort**值會控制應用程式要求從系統的任何可用的使用者連接埠時使用的最大連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="a6c81-107">The **MaxUserPort** value controls the maximum port number used when an application requests any available user port from the system.</span></span> <span data-ttu-id="a6c81-108">一般來說，存留較短的連接埠是從 1025 到 65535 之間配置範圍中。</span><span class="sxs-lookup"><span data-stu-id="a6c81-108">Normally, short-lived ports are allocated in the range from 1025 through 65535.</span></span> <span data-ttu-id="a6c81-109">連接埠範圍真正現在是範圍的起始點與結束點。</span><span class="sxs-lookup"><span data-stu-id="a6c81-109">The port range is now truly a range with a starting point and with an endpoint.</span></span> <span data-ttu-id="a6c81-110">新的預設開始連接埠是 49152，並預設結束連接埠為 65535。</span><span class="sxs-lookup"><span data-stu-id="a6c81-110">The new default start port is 49152, and the default end port is 65535.</span></span> <span data-ttu-id="a6c81-111">此範圍是除了由服務和應用程式所使用的已知通訊埠。</span><span class="sxs-lookup"><span data-stu-id="a6c81-111">This range is in addition to well-known ports that are used by services and by applications.</span></span> <span data-ttu-id="a6c81-112">在每部伺服器上，您可以修改伺服器使用的連接埠範圍。</span><span class="sxs-lookup"><span data-stu-id="a6c81-112">The port range that is used by the servers can be modified on each server.</span></span> <span data-ttu-id="a6c81-113">您可以調整這個範圍使用 netsh 命令，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a6c81-113">You adjust this range by using the netsh command, as follows:</span></span>  
  
 <span data-ttu-id="a6c81-114">**netsh int \<ipv4&#124;ipv6\>設定動態\<tcp&#124;udp\>啟動 = 數字的數字 = 範圍**</span><span class="sxs-lookup"><span data-stu-id="a6c81-114">**netsh int \<ipv4&#124;ipv6\> set dynamicport \<tcp&#124;udp\> start=number num=range**</span></span>  
  
 <span data-ttu-id="a6c81-115">此命令會設定為 TCP 動態連接埠範圍。</span><span class="sxs-lookup"><span data-stu-id="a6c81-115">This command sets the dynamic port range for TCP.</span></span> <span data-ttu-id="a6c81-116">開始連接埠是**數目**，而且連接埠總數**範圍**。</span><span class="sxs-lookup"><span data-stu-id="a6c81-116">The start port is **number**, and the total number of ports is **range**.</span></span> <span data-ttu-id="a6c81-117">以下是範例命令： 您可以使用下列 netsh 命令，以檢視動態連接埠範圍：</span><span class="sxs-lookup"><span data-stu-id="a6c81-117">The following are sample commands: You can view the dynamic port range by using the following netsh commands:</span></span>  
  
-   <span data-ttu-id="a6c81-118">netsh int ipv4 顯示動態 tcp。</span><span class="sxs-lookup"><span data-stu-id="a6c81-118">netsh int ipv4 show dynamicport tcp.</span></span> <span data-ttu-id="a6c81-119">若要增加到 tcp v4 的最大允許值的範圍內，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="a6c81-119">To increase the range to the maximum allowed value for tcp v4, use the following command:</span></span>  
  
     <span data-ttu-id="a6c81-120">**netsh int ipv4 設定動態 tcp 開始 = 1025 num = 64511**</span><span class="sxs-lookup"><span data-stu-id="a6c81-120">**netsh int ipv4 set dynamicport tcp start=1025 num=64511**</span></span>  
  
-   <span data-ttu-id="a6c81-121">netsh int ipv4 顯示動態 udp</span><span class="sxs-lookup"><span data-stu-id="a6c81-121">netsh int ipv4 show dynamicport udp</span></span>  
  
-   <span data-ttu-id="a6c81-122">netsh int ipv6 show 動態 tcp</span><span class="sxs-lookup"><span data-stu-id="a6c81-122">netsh int ipv6 show dynamicport tcp</span></span>  
  
-   <span data-ttu-id="a6c81-123">netsh int ipv6 show 動態 udp</span><span class="sxs-lookup"><span data-stu-id="a6c81-123">netsh int ipv6 show dynamicport udp</span></span>  
  
 <span data-ttu-id="a6c81-124">**TcpTimedWaitDelay**值決定的連接會保持在 TIME_WAIT 狀態下，在關閉時的時間長度。</span><span class="sxs-lookup"><span data-stu-id="a6c81-124">The **TcpTimedWaitDelay** value determines the length of time that a connection stays in the TIME_WAIT state when being closed.</span></span> <span data-ttu-id="a6c81-125">當連線處在 TIME_WAIT 狀態時，通訊端配對組不能重複使用。</span><span class="sxs-lookup"><span data-stu-id="a6c81-125">While a connection is in the TIME_WAIT state, the socket pair cannot be reused.</span></span> <span data-ttu-id="a6c81-126">因為這個值應該是兩次在網路上的最大的區段存留期，這是也稱為 2MSL 狀態。</span><span class="sxs-lookup"><span data-stu-id="a6c81-126">This is also known as the 2MSL state because the value should be twice the maximum segment lifetime on the network.</span></span> <span data-ttu-id="a6c81-127">如需詳細資訊，請參閱[網際網路 RFC 793](http://go.microsoft.com/fwlink/?LinkId=113719) (超連結"http://go.microsoft.com/fwlink/?LinkId=113719" http://go.microsoft.com/fwlink/?LinkId=113719)。</span><span class="sxs-lookup"><span data-stu-id="a6c81-127">For more information, see [Internet RFC 793](http://go.microsoft.com/fwlink/?LinkId=113719) ( HYPERLINK "http://go.microsoft.com/fwlink/?LinkId=113719" http://go.microsoft.com/fwlink/?LinkId=113719).</span></span> <span data-ttu-id="a6c81-128">若要調整 TcpTimedWaitDelay 設定，您必須修改登錄設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a6c81-128">To adjust the TcpTimedWaitDelay settings, you have to modify the registry settings as listed below:</span></span>  
  
###  
  
|||  
|-|-|  
|<span data-ttu-id="a6c81-129">索引鍵：</span><span class="sxs-lookup"><span data-stu-id="a6c81-129">Key:</span></span>|<span data-ttu-id="a6c81-130">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters</span><span class="sxs-lookup"><span data-stu-id="a6c81-130">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters</span></span>|  
|<span data-ttu-id="a6c81-131">值:</span><span class="sxs-lookup"><span data-stu-id="a6c81-131">Value:</span></span>|<span data-ttu-id="a6c81-132">TcpTimedWaitDelay</span><span class="sxs-lookup"><span data-stu-id="a6c81-132">TcpTimedWaitDelay</span></span>|  
|<span data-ttu-id="a6c81-133">資料類型：</span><span class="sxs-lookup"><span data-stu-id="a6c81-133">Data Type:</span></span>|<span data-ttu-id="a6c81-134">REG_DWORD</span><span class="sxs-lookup"><span data-stu-id="a6c81-134">REG_DWORD</span></span>|  
|<span data-ttu-id="a6c81-135">範圍：</span><span class="sxs-lookup"><span data-stu-id="a6c81-135">Range:</span></span>|<span data-ttu-id="a6c81-136">30-300 （十進位）</span><span class="sxs-lookup"><span data-stu-id="a6c81-136">30-300 (decimal)</span></span>|  
|<span data-ttu-id="a6c81-137">預設值︰</span><span class="sxs-lookup"><span data-stu-id="a6c81-137">Default value:</span></span>|<span data-ttu-id="a6c81-138">0x78 (120 十進位)</span><span class="sxs-lookup"><span data-stu-id="a6c81-138">0x78 (120 decimal)</span></span>|  
|<span data-ttu-id="a6c81-139">建議的值：</span><span class="sxs-lookup"><span data-stu-id="a6c81-139">Recommended value:</span></span>|<span data-ttu-id="a6c81-140">30</span><span class="sxs-lookup"><span data-stu-id="a6c81-140">30</span></span>|  
|<span data-ttu-id="a6c81-141">已有預設值？</span><span class="sxs-lookup"><span data-stu-id="a6c81-141">Value exists by default?</span></span>|<span data-ttu-id="a6c81-142">**否**，必須加入。</span><span class="sxs-lookup"><span data-stu-id="a6c81-142">**No**, needs to be added.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6c81-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6c81-143">See Also</span></span>  
 [<span data-ttu-id="a6c81-144">改善網路效能的一般指導方針</span><span class="sxs-lookup"><span data-stu-id="a6c81-144">General Guidelines for Improving Network Performance</span></span>](../technical-guides/general-guidelines-for-improving-network-performance.md)