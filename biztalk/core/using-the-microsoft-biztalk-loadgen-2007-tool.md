---
title: "使用 Microsoft BizTalk LoadGen 2007 工具 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LoadGen tool, how to
- LoadGen tool, test environments
ms.assetid: d1973a26-1c98-4261-bd9a-6357cdb19ccf
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b93018f093bbdffed64c44060f445a30d37344c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-microsoft-biztalk-loadgen-2007-tool"></a>使用 Microsoft BizTalk LoadGen 2007 工具
Microsoft BizTalk LoadGen 2007 工具是專門為開發人員及 IT 專業人員模擬 BizTalk Server 上的負載所設計。 使用此工具，您就可以模擬工具效能的負載以及 BizTalk 部署的負荷。 此外，開發人員還可以擴充此工具，以模擬自訂傳輸的負載。  
  
> [!NOTE]
>  LoadGen 2007 工具是下載[http://go.microsoft.com/fwlink/?LinkId=59841](http://go.microsoft.com/fwlink/?LinkId=59841)。 此工具的舊版，BizTalk Server 2004 負載產生工具是下載[http://go.microsoft.com/fwlink/?LinkId=108999](http://go.microsoft.com/fwlink/?LinkId=108999)。  
  
 此工具只能用於測試環境，不應使用於生產環境。 此工具是以「現況」提供，所以並不支援。  
  
> [!NOTE]
>  BizTalk Server 2004 負載產生工具可與 MSMQ 配接器搭配使用，但您必須執行其他某些步驟。 如需指示，請參閱[搭配 MSMQ 使用 LoadGen 2007](../core/using-loadgen-2007-with-msmq.md)。  
  
> [!NOTE]
>  64 位元電腦不支援 LoadGen。 您可以使用在 32 位元遠端電腦上執行的 LoadGen，針對 64 位元伺服器產生負載。  
  
## <a name="see-also"></a>另請參閱  
 [加速負載測試](../core/overdrive-load-test.md)