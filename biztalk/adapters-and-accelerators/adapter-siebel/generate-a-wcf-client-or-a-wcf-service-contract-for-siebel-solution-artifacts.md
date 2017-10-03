---
title: "產生 WCF 用戶端或 WCF 服務合約的 Siebel 方案成品 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- how to, generate a client class by using svcutil.exe
- creating a proxy
- how to, create a proxy
- WCF service model, creating a proxy
- how to, generate a client class by using the Add Adapter Service Reference Plug-in
- how to, generate a client class
ms.assetid: 52c32c86-6403-4bb4-9d43-1319d19a6b49
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c75615f0e6a3f6e4c947a7c13888558b7a666e77
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts"></a>產生 WCF 用戶端或 WCF 服務合約的 Siebel 方案成品
您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別針對 Siebel 成品中選取的作業。 您也可以使用 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別。不過，[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]公開 ServiceModel Metadata Utility Tool，透過標準的 Microsoft Windows 介面的功能。 它也提供不是使用 svcutil.exe 工具，可用的瀏覽和搜尋功能，並產生根據您選取當您連接至 Siebel 系統的繫結屬性的組態檔。  
  
## <a name="generating-a-wcf-client-class-by-using-the-add-adapter-service-reference-plug-in"></a>使用產生 WCF 用戶端類別新增配接器服務參考外掛程式  
 執行下列步驟來產生 WCF 用戶端類別使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
#### <a name="to-generate-a-wcf-client-class"></a>若要產生 WCF 用戶端類別  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]方案總管 中，以滑鼠右鍵按一下您的專案，然後**新增配接器服務參考**。  
  
2.  之後**新增配接器服務參考**對話方塊隨即開啟，請依照下列中的步驟[擷取 Siebel 作業在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)，連接至 Siebel 系統瀏覽和搜尋作業。 若要建立的作業，您選取的 WCF 用戶端類別，務必**用戶端 （輸出作業）**選取從**選取合約型別**下拉式清單 （這是預設值）。  
  
3.  在您選取的所有作業，您要為目標，請按一下之後**確定**產生 WCF 用戶端類別。  
  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]將兩個檔案加入至您的專案：  
  
-   WCF 用戶端程式碼檔案。 此檔案包含 WCF 用戶端類別和協助程式程式碼產生您所選取的作業。 第一次執行[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]它將會產生這個檔案的預設名稱**SiebelBindingClient.cs** 。 如果您再次執行它，它會產生的下一個檔案將會呼叫**SiebelBindingClient1.cs**。  數字尾碼會增加 1 的每一個您所產生的新檔案。  您也可以變更預設前置詞**SiebelBinding**輸入中的不同前置詞**檔案名稱前置詞**欄位[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]前，先選取**確定**至產生的檔案。  
  
-   **App.config**。這個檔案包含的繫結組態和設定的連接時所做的選擇為基礎的用戶端端點組態[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 App.config 檔案的內容的相關資訊，請參閱[設定 WCF 用戶端在 Siebel 系統](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md)。  
  
    > [!IMPORTANT]
    >  同時使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，如果您未指定類型字串的繫結屬性的值，且其預設值為 null 然後，繫結屬性將不會使用 app.config 檔案中。 您必須以手動方式繫結屬性和其值在 app.config 檔案中，視需要新增。  
  
## <a name="generating-a-wcf-client-class-by-using-svcutilexe"></a>使用 svcutil.exe 產生 WCF 用戶端類別  
 您可以使用 svcutil.exe 產生 WCF 用戶端類別，您的應用程式。 您必須設定要搭配使用 svcutil.exe [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。 如需有關設定和使用具有 svcutil.exe [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱[for Siebel eBusiness 應用程式中使用 BizTalk Adapter ServiceModel Metadata Utility Tool](../../adapters-and-accelerators/adapter-siebel/use-the-servicemodel-metadata-utility-with-the-siebel-adapter.md)。  
  
 Svcutil.exe 會產生 WCF 用戶端類別，在輸出檔案具有 output.cs 的預設檔案名稱。 您必須手動加入這個檔案中的您[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]專案。  
  
## <a name="see-also"></a>另請參閱  
 [開發 Siebel 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md)