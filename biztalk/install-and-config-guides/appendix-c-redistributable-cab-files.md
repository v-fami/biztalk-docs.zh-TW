---
title: 附錄 c： 可轉散發套件封包檔 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2049d61-e169-4b30-869a-33d5af097941
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b85d4a0dae708ef3f26304bce31ebd87fc230516
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023716"
---
# <a name="appendix-c-redistributable-cab-files"></a>附錄 C：可轉散發的封包檔
BizTalk Server 安裝程式會使用這些封包檔案。

## <a name="biztalk-2016-cab-files"></a>BizTalk 2016 封包檔

|語言|下載連結|  
|--------------|-------------------|  
|EN|<ul><li>**X64**<br /><br /> <ul><li>Windows Server 2016: [http://go.microsoft.com/fwlink/p/?LinkId=746413](http://go.microsoft.com/fwlink/p/?LinkId=746413)</li><li>Windows Server 2012 R2: [http://go.microsoft.com/fwlink/p/?LinkId=746412](http://go.microsoft.com/fwlink/p/?LinkId=746412)</li><li>Windows 10: [http://go.microsoft.com/fwlink/p/?LinkId=746408](http://go.microsoft.com/fwlink/p/?LinkId=746408)</li><li>Windows 8.1： [http://go.microsoft.com/fwlink/p/?LinkId=746411](http://go.microsoft.com/fwlink/p/?LinkId=746411)</li></ul></li><li>**X32**<br /><br /><ul><li>Windows 10: [http://go.microsoft.com/fwlink/p/?LinkId=746409](http://go.microsoft.com/fwlink/p/?LinkId=746409)</li><li>Windows 8.1： [http://go.microsoft.com/fwlink/p/?LinkId=746410](http://go.microsoft.com/fwlink/p/?LinkId=746410)</li></ul></li></ul>|  

> [!NOTE] 
> Windows 10 及 Windows Server 2016 和 Windows 8.1 及 Windows Server 2012 R2 使用相同的封包檔。 結果，它們會有相同的檔案名稱。

## <a name="biztalk-2013-r2-and-2013-cab-files"></a>BizTalk 2013 R2 和 2013 封包檔  

|語言|下載連結|  
|--------------|-------------------|  
|EN|<ul><li>**X64**<br /><br /> <ul><li>Windows Server 2012: [http://go.microsoft.com/fwlink/p/?LinkId=269616](http://go.microsoft.com/fwlink/p/?LinkId=269616)</li><li>Windows Server 2008: [http://go.microsoft.com/fwlink/p/?LinkId=269613](http://go.microsoft.com/fwlink/p/?LinkId=269613)</li><li>Windows 8: [http://go.microsoft.com/fwlink/p/?LinkId=269615](http://go.microsoft.com/fwlink/p/?LinkId=269615)</li><li>Windows 7: [http://go.microsoft.com/fwlink/p/?LinkId=269614](http://go.microsoft.com/fwlink/p/?LinkId=269614)</li></ul></li><li>**X32**<br /><br /> <ul><li>Windows 8: [http://go.microsoft.com/fwlink/p/?LinkId=269612](http://go.microsoft.com/fwlink/p/?LinkId=269612)</li><li>Windows 7: [http://go.microsoft.com/fwlink/p/?LinkId=269611](http://go.microsoft.com/fwlink/p/?LinkId=269611)</li></ul></li></ul>|  

## <a name="important-info"></a>重要資訊

- SQL XML 可能會有自己的軟體需求 (例如 `.NET Framework 3.5` 和 `.NET Framework 2.0`)，這些需求不包含在封包檔中。 如果 BizTalk Server 可以存取網際網路，則可能會自動安裝 SQL XML 軟體需求。 如果 BizTalk Server 不能存取網際網路，則會手動安裝 SQL XML 軟體需求。

- CAB 檔案安裝路徑也會列在**Setup.xml**安裝資料夾中的檔案 ([!INCLUDE[btsBizTalkServerPathx64_md](../includes/btsbiztalkserverpathx64-md.md)]\<您的版本\>)。

- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所需要的一些軟體，會在您執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝程式時，安裝在電腦上。  

- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝程式會讓您選擇從網站下載軟體必要元件，或從封包檔中解壓縮這些元件。 如果您選擇封包檔案，請先下載封包檔再執行安裝程式。  

- 您無法使用舊版 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的封包檔。 您必須從資料表中的連結下載封包檔。  

- 您無法透過 Telnet 工作階段下載封包檔。  
