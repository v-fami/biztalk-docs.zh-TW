---
title: "配接器和 BizTalk Server 中的快速鍵 |Microsoft 文件"
description: "所有配接器和在 BizTalk 中，包括內建配接器、 BAP、 HL7、 Swift、 RosettaNet、 FileAct，以及互動的加速器概觀"
caps.latest.revision: "3"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/09/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df7f26a1-e47b-4323-b9f0-58842c55a6f8
ms.author: mandia
ms.openlocfilehash: 30afb33621ed50af010c45edfb2643a24feaf91a
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="adapters-and-accelerators-in-biztalk-server"></a>配接器和 BizTalk Server 中的快速鍵
 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]包含不同的配接器和為您建立應用程式接收資料，並將資料傳送至不同的服務和 LOB 系統的快速鍵。 
 
本章節描述的不同配接器和適用於加速器[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。 

## <a name="out-of-the-box-adapters"></a>方塊外配接器
當您安裝 BizTalk Server 時，您也可以安裝會立即可用的內建配接器。 這些配接器包括檔案、 FTP、 MQ Series、 服務匯流排、 Logic Apps、 POP3、 SharePoint、 等等。

**[使用配接器](../core/using-adapters.md)列出的所有項目，而也示範如何使用每張介面卡。**
 
## <a name="biztalk-adapter-pack"></a>BizTalk 配接器封包
[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]隨附[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，並提供 WCF 配接器來連接您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Oracle、 SAP、 Siebel 和 SQL Server。 您也可以建立自己 WCF 架構的配接器使用[!INCLUDE[afproductnameshort_md](../includes/afproductnameshort-md.md)]。 

**請參閱[BizTalk Adapter Pack](../adapters-and-accelerators/biztalk-adapter-pack.md)安裝及設定這些配接器逐步教學課程和情況下，使用不同的配接器，建立應用程式及充分了解如何以 WCF 為基礎的服務處理訊息。**

## <a name="adapters-for-enterprise-applications"></a>Adapters for Enterprise Applications
這些配接器隨附於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 您可以使用這些介面卡連接 BizTalk Server 與 JD Edwards EnterpriseOne，JD Edwards OneWorld、 PeopleSoft Enterprise、 TIBCO Enterprise Message Service 和 TIBCO Rendezvous。

**請參閱[BizTalk Adapter for Enterprise Applications](biztalk-adapters-for-enterprise-applications.md)安裝及設定這些配接器逐步教學課程和案例中，建立應用程式使用不同的介面卡，等等。** 


## <a name="fileact-and-interact"></a>FileAct 和互動
[!INCLUDE[swift_adapter_md](../includes/swift-adapter-md.md)]隨附於[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，並提供之間的連線程式[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]和協會的全球 Interbank 財務 Telecommunication (SWIFT) 保護 IP 網路 (SIPN)。 

FileAct 配接器提供檔案及這些檔案的相關資訊的安全而可靠的交換。 

InterAct 配接器會提供安全、 可靠的訊息交換，個別結構化財務。 

**請參閱[FileAct 和 InterAct](../adapters-and-accelerators/fileact-interact/microsoft-biztalk-server-fileact-and-interact-adapters-documentation.md)來安裝和設定這些介面卡，逐步執行某些教學課程和案例，並取得充分的了解架構。** 

## <a name="hl7"></a>HL7

[!INCLUDE[btaBTAHL7NoNumber_md](../includes/btabtahl7nonumber-md.md)]隨附[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，並提供之間的連線程式[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]和醫療保健電腦健全狀況層級七 (HL7) 標準為基礎的應用程式。

**請參閱[HL7](../adapters-and-accelerators/accelerator-hl7/microsoft-biztalk-accelerator-for-hl7-documentation.md)安裝及設定配接器，逐步執行數個教學課程和案例，了解配接器的運作方式，以及使用不同的功能，包括結構描述、 通知、 批次處理、 驗證和更多。**

## <a name="rosettanet"></a>RosettaNet
BizTalk Accelerator for RosettaNet (BTARN) 隨附於 BizTalk Server 中，並簡化開發和部署的 RosettaNet 標準架構整合解決方案。 BTARN 支援 RosettaNet 實作架構 (RNIF);這是開放型的網路應用程式架構，讓商務夥伴協同執行 RosettaNet 夥伴介面程序 (Pip)。 

**請參閱[RosettaNet](../adapters-and-accelerators/accelerator-rosettanet/microsoft-biztalk-accelerator-for-rosettanet-documentation.md)若要深入了解此快速鍵，並使用與 BizTalk Server 解決方案。** 

## <a name="swift"></a>SWIFT
[!INCLUDE[btaA4SWIFTNoVersion_md](../includes/btaa4swiftnoversion-md.md)]隨附[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，並提供之間的連線您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]和協會的全球 Interbank 財務 Telecommunication (SWIFT) 訊息格式。

使用配接器與[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，客戶、 合作夥伴和系統整合者可以簡化開發、 部署和支援的整合方案的核心涵蓋了金融服務應用程式基礎結構和商務程序。

**請參閱[SWIFT](../adapters-and-accelerators/accelerator-swift/microsoft-biztalk-accelerator-for-swift-documentation.md)安裝及設定配接器，以逐步執行某些教學課程中，及使用訊息修復、 FIN 回應和 FRR 成品和更多。**

## <a name="get-some-help"></a>取得相關協助 
取得相關協助，並幫助其他人在[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]在論壇[http://go.microsoft.com/fwlink/p/?LinkId=87695](http://go.microsoft.com/fwlink/p/?LinkId=87695)。