---
title: 產生 WCF 用戶端或 Siebel 解決方案成品的 WCF 服務合約 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- how to, generate a client class by using svcutil.exe
- creating a proxy
- how to, create a proxy
- WCF service model, creating a proxy
- how to, generate a client class by using the Add Adapter Service Reference Plug-in
- how to, generate a client class
ms.assetid: 52c32c86-6403-4bb4-9d43-1319d19a6b49
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09cbd6fa8be325a31a6c3acd7ffb3c84092f9d63
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010903"
---
# <a name="generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts"></a>產生 WCF 用戶端或 Siebel 解決方案成品的 WCF 服務合約
您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]以產生 WCF 用戶端類別作為目標的 Siebel 成品中選取的作業。 您也可以使用 ServiceModel Metadata Utility Tool (svcutil.exe)，以產生 WCF 用戶端類別;不過，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]公開 ServiceModel Metadata Utility Tool，透過標準的 Microsoft Windows 介面的功能。 它也提供不是使用 svcutil.exe 工具，可用的瀏覽和搜尋功能，並產生組態檔，根據您選取當您連接至 Siebel 系統的繫結屬性。  
  
## <a name="generating-a-wcf-client-class-by-using-the-add-adapter-service-reference-plug-in"></a>產生 WCF 用戶端類別，使用 新增配接器服務參考外掛程式  
 執行下列步驟以產生 WCF 用戶端類別使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-generate-a-wcf-client-class"></a>若要產生 WCF 用戶端類別  
  
1. 在 [[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]方案總管] 中，以滑鼠右鍵按一下您的專案，然後**新增配接器服務參考**。  
  
2. 在後**新增配接器服務參考** 對話方塊隨即開啟，請依照中的步驟[擷取 Siebel 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)，連接至 Siebel 系統和瀏覽搜尋作業。 若要建立的作業，您選取的 WCF 用戶端類別，務必**用戶端 （傳出作業）** 從選取**選取合約的型別**（這是預設值） 的下拉式清單。  
  
3. 選取所有您想要為目標，請按一下作業後**確定**來產生 WCF 用戶端類別。  
  
   [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]將兩個檔案新增至您的專案：  
  
- WCF 用戶端程式碼檔案。 此檔案包含 WCF 用戶端類別和協助程式程式碼產生您所選取的作業。 第一次執行[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]它會產生此檔案的預設名稱**SiebelBindingClient.cs** 。 如果您再次執行它，它會產生下一個檔案將會呼叫**SiebelBindingClient1.cs**。  數字尾碼會增加 1，如您所產生的每個新檔案。  您也可以變更預設前置詞**SiebelBinding**輸入中的不同前置詞**檔案名稱前置詞**欄位[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]然後再選取**確定**至產生的檔案。  
  
- **App.config**。此檔案包含的繫結組態和設定的連接時所做的選取項目為基礎的用戶端端點組態[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 App.config 檔案的內容的相關資訊，請參閱[Siebel 系統設定 WCF 用戶端](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md)。  
  
  > [!IMPORTANT]
  >  同時使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，如果您未指定的字串類型的繫結屬性的值，而其預設值是 null，則該屬性繫結將無法使用 app.config 檔案中。 您必須手動加入的繫結屬性和其值在 app.config 檔案中，如有必要。  
  
## <a name="generating-a-wcf-client-class-by-using-svcutilexe"></a>使用 svcutil.exe 產生 WCF 用戶端類別  
 您可以使用 svcutil.exe 來產生 WCF 用戶端類別，您的應用程式。 您必須設定與 svcutil.exe [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。 如需有關設定及使用具有 svcutil.exe [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱 < [for Siebel eBusiness 應用程式，使用 BizTalk 配接器使用 ServiceModel Metadata Utility Tool](../../adapters-and-accelerators/adapter-siebel/use-the-servicemodel-metadata-utility-with-the-siebel-adapter.md)。  
  
 Svcutil.exe 會在 output.cs 的預設檔案名稱的輸出檔案中產生 WCF 用戶端類別。 您必須手動將此檔案中的您[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案。  
  
## <a name="see-also"></a>另請參閱  
 [開發使用 WCF 服務模型的 Siebel 應用程式](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)