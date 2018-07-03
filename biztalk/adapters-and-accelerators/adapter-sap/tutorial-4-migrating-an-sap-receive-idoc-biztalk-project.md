---
title: 教學課程 4： 移轉 SAP 接收 IDOC BizTalk 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- migration, SAP Receive IDOC BizTalk project
- migrating, SAP Receive IDOC BizTalk project
- migration
ms.assetid: 74b667d8-2d8c-4c15-9dd2-f13521404b85
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e943c3663767d2b684b0f4657f639d752705b86f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011255"
---
# <a name="tutorial-4-migrating-an-sap-receive-idoc-biztalk-project"></a>教學課程 4： 移轉 SAP 接收 IDOC BizTalk 專案
不同於以 WCF 為基礎的 SAP 配接器隨附於 Microsoft BizTalk Server 舊版[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]在許多方面，包括：  
  
- 建立 BizTalk 專案的設計階段經驗。  
  
- 中繼資料的擷取體驗。  
  
- 結構描述檔案名稱和命名空間。  
  
- 資料類型對應。  
  
- 可以使用配接器執行的作業。  
  
- 在 BizTalk Server 管理主控台中的實體連接埠組態。  
  
  中的主題會說明這些差異[移轉 BizTalk 專案建立使用上一個版本的 SAP 配接器](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37)。  
  
  不過，您可以對使用舊版的配接器建立 BizTalk 專案中的變更，並讓其使用以 WCF 為基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
  本教學課程會提供指示，您應該對現有的 BizTalk 專案使用舊版的配接器所建立的變更。  
  
> [!NOTE]
>  在本教學課程中，為了保持簡潔，舊版的 SAP 配接器會稱為 vPrev SAP 配接器。 同樣地，使用 vPrev SAP 配接器的 BizTalk 專案會被稱為 vPrev BizTalk 專案。  
  
## <a name="sample-used-for-the-tutorial"></a>用於本教學課程的範例  
 本教學課程是以示範如何將 SAP 系統從接收一般檔案 IDOC vPrev BizTalk 專案的範例 (ReceiveIDOC_Migration) 為基礎。 提供了範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您必須具有 vPrev BizTalk 專案。 本教學課程中牽涉到從 SAP 系統接收 ORDERS03 IDOC BizTalk 專案。  
  
-   [建立強式名稱金鑰檔案，並了解工具](../../adapters-and-accelerators/adapter-sap/prerequisites-to-create-sap-applications.md)

  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>了解 BizTalk 專案使用舊版配接器的建立  
 接收 IDOC vPrev BizTalk 專案的關鍵要素是：  
  
-   **BizTalk 協調流程**。 這是一項簡單的 SAP 所組成的協調流程接收埠從 SAP 系統接收一般檔案 IDOC。 BizTalk 專案包含要轉換成 XML 的 一般檔案 IDOC 一般檔案解譯器，以便用於協調流程。 XML IDOC 會複製到檔案位置透過 file 連接埠之前，它會轉換回使用一般檔案組合器的一般檔案 IDOC。  
  
-   **您想要傳送至 SAP 系統的 IDOC 的結構描述**。 本教學課程中，牽涉到從 SAP 系統接收 ORDERS03 IDOC BizTalk 專案。 產生的 IDOC 的結構描述是 ORDERS03.xsd。 此結構描述是使用 vPrev SAP 配接器所產生的。  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>如何移轉 BizTalk 專案可讓您建立使用舊版的配接器  
 本移轉教學課程的目標是要讓您從 SAP 系統，而不傳送埠使用 Wcf-custom 傳送埠，vPrev SAP 配接器的接收一般檔案 IDOC。 之前了解哪些設定所需的 Wcf-custom 傳送埠，您必須先了解哪些實體連接埠所需的 vPrev 傳送 IDOC 的協調流程。  
  
- VPrev SAP 接收從 SAP 系統接收一般檔案 IDOC 的連接埠。 連接埠也會將此轉換使用一般檔案解譯器，也就是 可用 XML IDOC vPrev BizTalk 應用程式的一部分。 XML IDOC 符合結構描述 (ORDERS03.xsd)，您就會產生使用 vPrev SAP 配接器。  
  
- 它將會複製到資料夾的 IDOC 的 file 傳送埠。 此連接埠也會使用一般檔案組合器的 BizTalk 應用程式中，您可以使用管線將 XML IDOC 轉換成一般檔案 IDOC。  
  
  若要移轉您現有的 vPrev BizTalk 專案，您不需要變更檔案傳送埠，以將一般檔案 IDOC 複製到資料夾。 您只需要設定新 WCF 自訂接收連接埠，以正確的組態設定。 本教學課程示範如何設定 Wcf-custom 接收埠以使用以 WCF 為基礎的 SAP 系統接收 Idoc [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1：建置並部署 vPrev BizTalk 專案以便接收 IDOC](../../adapters-and-accelerators/adapter-sap/step-1-build-and-deploy-the-vprev-biztalk-project-for-receiving-an-idoc.md)  
  
-   [步驟 2：設定 Wcf-Custom 單向接收埠](../../adapters-and-accelerators/adapter-sap/step-2-configure-a-wcf-custom-one-way-receive-port.md)  
  
-   [步驟 3：測試已移轉的應用程式](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application5.md)  
  
## <a name="see-also"></a>另請參閱  
 [SAP 配接器教學課程](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)