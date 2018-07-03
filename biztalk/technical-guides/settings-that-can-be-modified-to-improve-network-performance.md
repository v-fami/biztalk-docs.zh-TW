---
title: 您可以修改以改善網路效能的設定 |Microsoft Docs
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
ms.openlocfilehash: 2a21cc6339c82ab5465f117c8ef51d539add0055
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016257"
---
# <a name="settings-that-can-be-modified-to-improve-network-performance"></a>您可以修改以改善網路效能的設定
本主題會提供影響網路效能的建議值的描述。  
  
> [!IMPORTANT]  
>  在完成本指南中的效能測試它發現，Windows Server 2008，會顯示預設微調。 修改登錄設定，才應該執行對系統影響仔細分析之後。  
  
## <a name="adjust-the-maxuserport-and-tcptimedwaitdelay-settings"></a>調整 MaxUserPort 以及 TcpTimedWaitDelay 的設定  
 **MaxUserPort**值會控制應用程式向系統要求的任何可用的使用者連接埠時使用的最大的連接埠號碼。 一般來說，短期配置連接埠範圍： 1025 到 65535 之間。 連接埠範圍是現在真正範圍的起始點與結束點。 新的預設開始連接埠是 49152，並預設結束連接埠為 65535。 此範圍是除了由服務和應用程式所使用的已知連接埠。 在每一部伺服器上，您可以修改伺服器所使用的連接埠範圍。 您可以調整這個範圍，如下所示使用 netsh 命令：  
  
 **netsh int \<ipv4&#124;ipv6\>設定動態\<tcp&#124;udp\>開始 = 數字的 num = 範圍**  
  
 此命令會設定為 TCP 動態連接埠範圍。 開始連接埠**數字**，和連接埠總數**範圍**。 以下是命令範例： 您也可以使用下列 netsh 命令來檢視 「 動態連接埠範圍：  
  
- netsh int ipv4 顯示動態 tcp。 若要增加到 tcp v4 的最大允許值的範圍內，使用下列命令：  
  
   **netsh int ipv4 設定動態 tcp 啟動 = 1025 num = 64511**  
  
- netsh int ipv4 顯示動態 udp  
  
- netsh int ipv6 顯示動態 tcp  
  
- netsh int ipv6 顯示動態 udp  
  
  **TcpTimedWaitDelay**值決定的連接會保持在 TIME_WAIT 狀態下，正在關閉時的時間長度。 當連線處在 TIME_WAIT 狀態時，不能重複使用通訊端配對組。 因為此值應該是兩次在網路上的最大的區段存留期，這是也稱為 2MSL 狀態。 如需詳細資訊，請參閱 <<c0> [ 網際網路 RFC 793](http://go.microsoft.com/fwlink/?LinkId=113719) (HYPERLINK"<http://go.microsoft.com/fwlink/?LinkId=113719>" <http://go.microsoft.com/fwlink/?LinkId=113719>)。 若要調整 TcpTimedWaitDelay 的設定，您必須修改登錄設定，如下所示：  
  
###  
  
|||  
|-|-|  
|索引鍵：|HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters|  
|值:|TcpTimedWaitDelay|  
|資料類型：|REG_DWORD|  
|範圍：|30-300 （十進位）|  
|預設值︰|0x78 (120 十進位)|  
|建議的值：|30|  
|根據預設，存在值？|**否**，需要加入。|  
  
## <a name="see-also"></a>另請參閱  
 [改善網路效能的一般指導方針](../technical-guides/general-guidelines-for-improving-network-performance.md)