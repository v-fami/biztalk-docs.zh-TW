---
title: "BizTalk Adapter for Siebel 電子商務應用程式，在 BizTalk 中的詞彙 |Microsoft 文件"
description: "常見的詞彙和定義 Siebel 配接器在 BizTalk Adapter pack (BAP) 中使用"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75c74760-53b6-45c3-bacc-bb7ab4fb5b4b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54cb0b66bc7cb4b7477160ab2673ec06165ee6c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="terms-and-definitions-for-the-siebel-adapter"></a>詞彙和定義 Siebel 配接器
下列詞彙和定義會用於[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。  
  
 
## <a name="a"></a>只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，  

**配接器**  
WCF 架構的元件，可協助 exchange 應用程式 （例如，特定業務系統） 之間的訊息和 BizTalk Server。 配協器由設計階段元件和執行階段元件組成，進行接收和傳送的作業。

**配接器用戶端**  
應用程式透過配接器的特定業務 (LOB) 系統進行互動。  

  
## <a name="b"></a>B
  
**繫結**  
軟體元件與軟體層連結在一起的程序。 安裝網路元件時，便會建立元件的繫結關聯性與相依性。 繫結使元件得以彼此通訊。 在 BizTalk Server 中，此為協調流程配接器-不特定結束點 (連接埠或角色連結) 與實體配接器-特定結束點 (傳送埠/接收埠或合作對象) 之間的已建立對應。

**BizTalk Server**  
連接各種不同的軟體。 BizTalk Server 可讓您建立和修改處理程序邏輯會使用該軟體。 BizTalk Server 也可讓資訊工作者監控執行中的處理程序、與企業合作夥伴互動並執行其他業務相關工作。

 
## <a name="c"></a>C
  
**通道**  
繫結項目的實體實作。 繫結表示組態，通道則是與該組態相關聯的實作。 因此，沒有與每個繫結項目相關聯的通道。 通道堆疊在彼此的上方來建立繫結的實體實作： 通道堆疊。

**連線 URI**  
識別分散式環境中的資源字串。 配接器使用的連接統一資源識別元 (URI)，其中包含建立與 LOB 系統的連線所需的資訊。

**合約**  
指定集合與存取服務所提供的作業所需的訊息結構。  
  
## <a name="d"></a>D
  
**設計階段經驗**  
程序和開發人員在設計階段; 可以執行的作業例如，使用取用配接器服務 BizTalk 專案增益集來擷取訊息結構描述。 

 
## <a name="e"></a>E 
  
**端點位址**  
網路位址，用於識別 Windows Communication Foundation (WCF) 服務端點的位置。 配接器，表示端點位址做為統一資源識別元 (URI) 包含參數的位置和連接的連接。 配接器可以使用它們來連接到基礎的特定業務 (LOB) 系統。

**企業單一登入系統 (SSO)**  
SSO 資料庫、主要密碼伺服器以及一或多個企業單一登入 (SSO) 伺服器。 這些伺服器會在 Windows 與非 Windows 認證間進行對應，在 SSO 資料庫中尋找認證，然後用來管理 SSO 系統。 SSO 資料庫也做為組態存放區，保留配接器的自訂組態資料。

**可延伸標記語言 (XML)**  
標記語言，設計用來描述資料。 不會預先定義的 XML 標記。  
 
 
## <a name="g"></a>G
  
**全域組件快取 (GAC)**  
整個電腦的程式碼快取，它會存放供電腦上多個應用程式共用而特別安裝的組件。 在全域組件快取中部署的應用程式必須具有強式名稱。
  
 
## <a name="i"></a>I
  
**輸入的作業**  
介面卡上的特定業務 (LOB) 系統所叫用作業。  
  
## <a name="m"></a>M
  
**中繼資料**  
在 WCF 中，指的服務所公開的合約描述。 這就所謂的服務描述，並表示 WSDL 文件中。 配接器所公開的中繼資料描述 （介面），它可以在基礎 LOB 系統上執行的作業。 如位置、時間、訊息大小和 (或) 例外資訊等資訊。


**[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]**  
建置 BizTalk 配接器使用 Web 服務為基礎的開放式標準規格。  
  
## <a name="o"></a>O
  
**單向**  
寄件者會傳送一則訊息，但沒有回應的訊息交換模式 (MEP) 會傳回收件者。 在 BizTalk Server 中，Mep 稱為通訊模式。

**輸出作業**  
作業的特定業務系統 (LOB) 配接器所叫用。

**output.cs**  
ServiceModel Metadata Utility 工具 (svcutil.exe) 所建立之預設輸出檔案。  
 
## <a name="p"></a>P
  
**挑選清單**  
其值通常限制為一組值 （類似於列舉型別） 的其中一個商務元件中的欄位。

**proxy**  
在 WCF 中，是指實作服務所公開的服務合約的 managed 程式碼物件。 WCF 服務模型根據使用這類的 proxy。 在 WCF 服務模型中，.NET 介面來表示服務合約。
  
## <a name="r"></a>R
  
**要求-回應**  
訊息交換模式 (MEP) 寄件者傳送要求訊息與預期來自接收者的回應訊息。 在 BizTalk Server 中，Mep 稱為通訊模式。 根據訊息的技術和 （輸入或輸出） 的要求訊息的方向，此模式也稱為要求-回覆或請求-回應。

**執行階段體驗**  
程序和執行階段期間或部署解決方案; 時，開發人員所執行的作業例如，從 BizTalk Server 管理主控台建立實體連接埠繫結。  


## <a name="s"></a>S
  
**結構描述**  
訊息的結構。 結構描述可以包含多個 ubschema。

**ServiceModel Metadata Utility Tool (svcutil.exe)**  
命令列公用程式所包含的 WCF。 它用來建立服務模型 proxy 程式碼，例如配接器的 WCF 服務所公開的服務描述 （中繼資料）。 若為輸出的作業，此工具會建立 WCF 用戶端類別和協助程式程式碼;輸入的作業，此工具會建立 WCF 服務合約和協助程式程式碼。

**Siebel 商務元件**  
關聯邏輯上相關的資料行從一個或多個資料表成單一結構。

**Siebel 商務物件**  
代表商務元件的邏輯群組。
  
**Siebel 商務服務**  
商務服務方法或可以在 Siebel 系統中直接叫用的函式的集合。
  
**Siebel COM 資料控制項程式庫**  
包含介面，可讓外部用戶端類似 Siebel 配接器連線並通訊以 Siebel 應用程式物件管理員 Siebel 伺服器上。

**SOAP （簡易物件存取通訊協定）**  
簡單、 以 XML 為基礎的通訊協定，交換結構化，和在分散式環境中輸入資訊。 WCF 為基礎的用戶端和服務來叫用作業，並傳回結果之間的 SOAP 訊息交換。

**SOAP 訊息**  
格式正確的 XML 文件。 此文件應使用 SOAP 信封和 SOAP 編碼命名空間，且包含選擇性 XML 宣告，後面接著由選擇性 SOAP 標頭與 SOAP 訊息內文所構成的 SOAP 信封 (根項目)。

**SQL Server Integration Services (SSIS)**  
此元件可用於匯入、 匯出及轉換來自不同資料來源的資料。 先前稱為資料轉換服務 (DTS)。

**強型別資料**  
資料集或結果集繫結至基礎的物件型別。 強型別 XML 資料集的每個資料列被由型別，名為基礎的物件類型的欄位對應的項目。  
  
## <a name="w"></a>W
  
**WCF 通道模型**  
程式設計模型依賴多個介面和其他類型。 通道會提供低階的程式設計模型，來傳送和接收訊息。
  
**WCF 用戶端**  
用戶端應用程式建構，可公開為方法的服務作業。 您可以使用 新增配接器服務參考 Visual Studio 外掛程式或 ServiceModel Metadata Utility Tool 從配接器所公開的中繼資料產生 WCF 用戶端類別。

**WCF 服務合約**  
服務合約的 managed 程式碼表示法。 這會表示為介面中的類別和方法的屬性會設定來定義服務、 作業、 訊息，以及用來與服務通訊的資料合約。 您可以使用 ServiceModel 中繼資料公用程式工具 」 或 「 新增配接器服務參考 Visual Studio 外掛程式，從配接器所公開的中繼資料產生 WCF 服務合約。 您實作 WCF 服務合約以接收來自 LOB 系統的作業。

**WCF 服務模型**  
WCF 程式撰寫模型，服務以 managed 程式碼物件。 服務所公開的作業會表示為具有強型別資料的方法。

**弱型別資料**  
資料集或未繫結至基礎的物件類型的結果集。 弱型別 XML 資料集的每個資料列所組成的屬性描述的名稱和每個項目類型的泛型資料行集合。

**web 服務**  
應用程式邏輯單元，對其他應用程式提供資料和服務。 應用程式使用標準 Web 通訊協定和資料格式 (如 HTTP、XML 和 SOAP) 存取 XML Web 服務，與每個 XML Web 服務實作的方式無關。 XML Web 服務結合元件基礎開發和 Web 的最佳層面，是 .NET 程式開發模型的基石。

**Web 服務描述語言**  
XML 架構語言描述為一組端點運作的服務，在訊息上。 WSDL 文件描述服務合約、 作業合約、 訊息合約和用戶端必須使用的資料合約與服務的介面。

**Windows Communication Foundation (WCF)**  
Microsoft 服務導向的通訊基礎結構。 原本就是，架構會提供用戶端與服務程式設計模型和程式設計模型進行更細微的控制訊息交換的通道。

**WS 中繼資料交換 (MEX) 端點**  
它會實作 WCF 服務，例如配接器，所公開的端點**IMetadataExchange**介面。 WS 中繼資料交換端點可用來擷取服務描述 (WSDL) 中的目標系統上的配接器所公開的作業。 |  
  
## <a name="x"></a>X
**XML 結構描述定義語言 (XSD)**  
結構描述語言。 XML 結構描述定義元素、 屬性和資料類型符合全球資訊網協會 (W3C) XML 結構描述第 1 部分： 結構建議事項，XML 結構描述定義語言。 「W3C XML Schema Part 2: Datatypes Recommendation」則針對定義 XML 結構描述中所使用的資料類型提供建議。 XML 結構描述定義語言讓您定義 XML 訊息的結構和資料類型。
