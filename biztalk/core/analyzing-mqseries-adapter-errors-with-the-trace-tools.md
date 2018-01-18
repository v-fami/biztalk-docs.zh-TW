---
title: "分析的追蹤工具的 MQSeries 配接器錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Adapter Trace Utility, about Adapter Trace Utility
- Adapter Trace Utility, installing
- installing, Adapter Trace Utility
- Adapter Trace Utility, enabling
- errors, MQSeries adapters
- MQSeries adapters, Adapter Trace Utility
- Adapter Trace Utility, running
- MQSeries adapters, errors
- Adapter Trace Utility
ms.assetid: fdc73d99-3b73-491d-9b2f-7064364fefa7
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b53d1d2c0bbe19c54804b553041f8dc9ae4db20c
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="analyzing-mqseries-adapter-errors-with-the-trace-tools"></a>使用追蹤工具分析 MQSeries 配接器錯誤
您可以使用追蹤工具來分析執行應用程式時的傳訊失敗。 透過 MQSeries 配接器，您必須使用兩個工具，一個是供配接器及您的 BizTalk 應用程式使用的工具 (trace.cmd)，另一個則是供 MQSAgent 使用的工具 (MQSTrace.cmd)。 這兩種工具都會使用 tracelog.exe。 如果尚未安裝 tracelog.exe，您就必須安裝該檔案。  
  
 使用 trace.cmd 與 MQSTrace.cmd，您必須設定一個選項 (**-工具**)，因此這些工具可以找到 tracelog.exe 檔案。  
  
## <a name="install-the-trace-utility"></a>安裝追蹤公用程式  
 若要安裝「BizTalk 配接器追蹤公用程式」，請依照下列步驟：  
  
1.  若要下載 Tracelog.exe 檔案，請瀏覽 Microsoft Platform SDK 下載網站，網址 [http://go.microsoft.com/fwlink/?LinkId=21975](http://go.microsoft.com/fwlink/?LinkId=21975)。  
  
2.  按一下連結來啟動 Platform SDK Web 安裝程式 **x86.exe** 底部的 [Web] 頁面的檔案。  
  
3.  當提示出現時，請選擇自訂安裝選項。  
  
4.  在 **[自訂安裝]** 對話方塊中，按一下以清除所有可用的功能。  
  
5.  展開 **[Microsoft Windows Core SDK]** 功能，然後展開 **[工具]** 功能。  
  
6.  選擇 **[工具 (Intel 64 位元)]** 功能，然後按一下 **[將會安裝至本機硬碟]**。  
  
7.  按 **[下一步]**，然後再按 **[下一步]** ，以開始安裝。  
  
8.  找出 *機*:\\*MicrosoftPlatformSDKInstallationFolder\bin* 資料夾，然後再將複製到 Microsoft BizTalk Server 安裝資料夾 Tracelog.exe 檔案。 BizTalk Server 安裝資料夾也包含 Trace.cmd 檔案。  
  
## <a name="enable-the-trace-utility"></a>啟用追蹤公用程式  
 若要啟用 BizTalk Server 中的「BizTalk 配接器追蹤公用程式」，請依照下列步驟：  
  
1.  移到包含 trace.cmd 的目錄。 預設位置是 Microsoft BizTalk Server 目錄。  
  
2.  輸入下列命令，並將括號括住的目錄以您電腦上包含 tracelog.exe 檔案的目錄替代，然後按 ENTER。  
  
     **trace-tools"c:\Program Files\Microsoft SDK\Bin"**  
  
3.  移到包含 MQSTrace.cmd 的目錄。  
  
4.  輸入下列命令，並將括號括住的目錄以您電腦上包含 tracelog.exe 檔案的目錄替代，然後按 ENTER。  
  
     **MQSTrace-tools"c:\Program Files\Microsoft SDK\Bin 」**  
  
## <a name="run-the-trace-utility"></a>執行追蹤公用程式  
 若要執行「BizTalk 配接器追蹤公用程式」，請依照下列步驟：  
  
1.  在命令提示字元中，輸入 **trace.cmd-start-high**, ，然後按 ENTER 鍵。  
  
2.  執行失敗的實例。  
  
3.  在命令提示字元中，輸入 **trace.cmd-停止**, ，然後按 ENTER 鍵。  
  
4.  bts2006.bin 檔案包含追蹤工具的輸出。 請連絡 Microsoft 產品支援服務以取得分析。 如需詳細資訊，請參閱 [http://go.microsoft.com/fwlink/?LinkId=41645](http://go.microsoft.com/fwlink/?LinkId=41645)。  
  
 若要執行 MQSAgent 追蹤公用程式，請依照下列步驟：  
  
1.  在命令提示字元中，輸入 **MQSTrace.cmd-start-high**, ，然後按 ENTER 鍵。  
  
2.  執行失敗的實例。  
  
3.  在命令提示字元中，輸入 **MQSTrace.cmd-停止**。  
  
4.  MQSAdapterTrace.bin 檔案包含追蹤工具的輸出。 請連絡 Microsoft 產品支援服務以取得分析。 如需詳細資訊，請參閱 [http://go.microsoft.com/fwlink/?LinkId=41645](http://go.microsoft.com/fwlink/?LinkId=41645)。