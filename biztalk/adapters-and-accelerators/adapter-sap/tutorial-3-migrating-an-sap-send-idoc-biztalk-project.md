---
title: 教學課程 3： 移轉 SAP 傳送 IDOC 的 BizTalk 專案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- migrating, SAP Send IDOC BizTalk project
- migration
ms.assetid: c0a11432-5388-4054-8996-08a957cc02eb
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52f8bc638d1adefe952ce055542706d11e0ca61f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217038"
---
# <a name="tutorial-3-migrating-an-sap-send-idoc-biztalk-project"></a>教學課程 3： 移轉 SAP 傳送 IDOC BizTalk 專案
SAP 配接器隨附於 Microsoft BizTalk Server 的先前版本不同於 WCF 基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]在許多方面，包括：  
  
-   建立 BizTalk 專案的設計階段經驗。  
  
-   中繼資料擷取的經驗。  
  
-   結構描述檔案名稱和命名空間。  
  
-   資料類型對應。  
  
-   可以使用配接器中執行的作業。  
  
-   在 BizTalk Server 管理主控台中的實體連接埠設定。  
  
 中的主題將說明這些差異所[移轉 BizTalk 專案建立使用上一個版本的 SAP 配接器](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37)。  
  
 不過，您可以使用舊版的配接器所建立的 BizTalk 專案中進行變更並讓它運作以 WCF 為基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
 本教學課程提供指示應該對現有的 BizTalk 專案使用舊版的配接器所建立的變更。  
  
> [!NOTE]
>  在此教學課程中，為了簡短起見，舊版的 SAP 配接器將會稱為 vPrev SAP 配接器。 同樣地，使用 vPrev SAP 配接器的 BizTalk 專案將被稱為 vPrev BizTalk 專案。  
  
## <a name="sample-used-for-the-tutorial"></a>教學課程使用範例  
 本教學課程根據範例 (SendIDOC_Migration)，示範如何移轉傳送 IDOC 到 SAP 系統的 vPrev BizTalk 專案。 此範例隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您必須 vPrev BizTalk 專案。 本教學課程包含傳送 BOMDOC IDOC 到 SAP 系統的 BizTalk 專案。  
  
-   您必須使用 vPrev SAP 配接器之 SAP 系統傳送一般檔案 BOMDOC IDOC。 在此教學課程提供的範例包含這個一般檔案 IDOC。  
  
-   [建立強式名稱金鑰檔，並了解工具](../../adapters-and-accelerators/adapter-sap/prerequisites-to-create-sap-applications.md)
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>了解 BizTalk 專案建立使用配接器的先前版本  
 傳送 IDOC vPrev BizTalk 專案的關鍵要素是：  
  
-   **BizTalk 協調流程**。 這是簡單的協調流程，從檔案位置挑選一般檔案 IDOC，並將傳送至 SAP 系統，使用 SAP IDOC 的傳送埠。 BizTalk 專案包含要轉換為 XML，一般檔案 IDOC 一般檔案解譯器，使其可以用於協調流程中。 XML IDOC 由 vPrev SAP 傳送埠之前，會將它轉換回使用一般檔案組合器的一般檔案 IDOC。  
  
-   **您想要傳送至 SAP 系統的 idoc 的結構描述**。 此教學課程中，您需要傳送 BOMDOC01 IDOC 至 SAP 系統的 BizTalk 專案。 產生 idoc 的結構描述是 BOMDOC01.xsd。 此結構描述會產生使用 vPrev SAP 配接器。  
  
-   **一般檔案 IDOC**。 這是傳送到 SAP 系統的一般檔案 IDOC。  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>使用舊版的配接器如何移轉 BizTalk 專案建立  
 本移轉教學課程的目標是讓您將傳送到 SAP 系統，而不傳送埠使用 Wcf-custom 傳送埠 vPrev SAP 配接器的一般檔案 IDOC。 之前了解哪些設定所需的 Wcf-custom 傳送埠，您必須先了解哪些實體連接埠所需的 vPrev 傳送 IDOC 的協調流程：  
  
-   File 接收挑選一般檔案 IDOC 的連接埠。 此連接埠會使用一般檔案解譯器管線中的 BizTalk 應用程式，可用來將一般檔案轉換成符合結構描述 (BOMDOC01.xsd) 使用 vPrev SAP 配接器所產生的 XML。  
  
-   SAP vPrev 傳送埠傳送一般檔案 IDOC 至 SAP 系統。 在傳送之前一般檔案，連接埠會使用一般檔案組合器將 XML IDOC 轉換成一般檔案 IDOC。  
  
 若要移轉現有的 vPrev BizTalk 專案，您不需要變更檔案接收埠挑選一般檔案 IDOC，並將一般檔案 IDOC 轉換為使用一般檔案解譯器的 XML。 您只需要以正確的組態設定來設定新的 WCF 自訂傳送連接埠。 本教學課程示範如何設定 Wcf-custom 傳送埠傳送 Idoc 至 SAP 系統使用 WCF 型[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1： 建立和部署傳送 IDOC vPrev BizTalk 專案](../../adapters-and-accelerators/adapter-sap/step-1-build-and-deploy-the-vprev-biztalk-project-for-sending-an-idoc.md)  
  
-   [步驟 2： 設定 Wcf-custom 單向傳送埠](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-send-port.md)  
  
-   [步驟 3： 測試已移轉的應用程式](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application2.md)  
  
## <a name="see-also"></a>另請參閱  
 [SAP 配接器教學課程](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)