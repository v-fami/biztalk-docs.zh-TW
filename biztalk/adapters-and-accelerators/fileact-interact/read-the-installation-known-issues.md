---
title: 閱讀安裝已知問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 245379f2-4048-4803-83ea-38dc23eb1a81
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4bc572cc18ca7d9d5515fe9f189287df5d1440f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022948"
---
# <a name="read-the-installation-known-issues"></a>閱讀安裝已知問題
[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] 有列在下列各節中的已知的問題。  
  
## <a name="swift-does-not-support-stress-testing-on-integration-test-bed-itb-and-swiftnet-stub-environment"></a>SWIFT 不支援整合測試平台 (ITB) 和 SWIFTNet 虛設常式環境測試的壓力  
 ITB 不提供以輸送量，服務等級協定 (SLA)，而且無法保證資料是完全傳輸，或是一致。 您應該實作到實際執行網路試驗環境中的壓力測試。  
  
 此外，您必須確定所有節點 （伺服器、 線條和頻寬） 已正確設定以避免遺失任何資料。 以下是典型的範例輸送量：  
  
- Fileact 互動傳送使用量較大的電腦 下： 20 的訊息/分鐘  
  
- 互動/Fileact 接收使用量較大的電腦 下： 300-400 訊息/分鐘  
  
  如需詳細資訊，請參閱您 SWIFT 的文件。  
  
## <a name="messages-not-pushed-when-queue-is-open"></a>開啟佇列時不會發送的訊息  
 當您使用互動或 FileAct 儲存和轉寄 (SnF) 模式中，如果佇列的工作階段已開啟，而且不會發送訊息時，您必須重新 SNLreceiver.exe。 這可避免 SWIFT 可能偶爾發生的問題。  
  
## <a name="you-must-use-cdata-when-passing-characters-like--and--in-message"></a>您必須使用 CDATA 當傳遞字元像是"<"和"&"訊息  
 CDATA 會使用不應由 XML 剖析器剖析的文字資料的相關詞彙。  字元像是"<"和"&"是不合法的 XML 項目中。 "<"會產生錯誤，因為剖析器將它解譯為新項目的開頭。 "&"會產生錯誤，因為剖析器將它解譯為開頭的字元實體。 剖析器會忽略 CDATA 區段內的所有項目。 CDATA 區段的開頭 「\<！ [CDATA ["和結尾是"]]\>"  
  
## <a name="you-must-use-passthrough-pipelines-with-payload-only-mode"></a>您必須使用 Passthrough 管線具有僅限裝載模式  
 如果您使用僅限裝載模式 InterAct 配接器，您必須使用通過管線，在這兩個傳送和接收埠，如果您不想要使用自訂管線。  
  
## <a name="multiple-security-contexts-not-created-swiftnet-stub-computer"></a>無法建立 （SWIFTNet 虛設常式電腦） 的多個安全性內容  
 SWIFTNet 虛設常式的電腦上，多個安全性內容不會針對不同的傳送埠。 ITB 上建立多個安全性內容。