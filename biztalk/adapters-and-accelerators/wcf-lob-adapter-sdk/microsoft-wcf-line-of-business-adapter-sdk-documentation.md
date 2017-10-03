---
title: "Microsoft Windows Communication Foundation 線條的商務配接器 SDK 文件 |Microsoft 文件"
description: "快速安裝、 開始、 規劃和設計、 開發、 連結和疑難排解 WCF LOB 配接器 SDK 在 BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a2b098c-ef41-4cc0-8063-1fd043f1176f
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8472fb56beab8f6d86ff33bebb9171d09d503ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="microsoft-windows-communication-foundation-line-of-business-adapter-sdk-documentation"></a>Microsoft Windows Communication Foundation 線條的商務配接器 SDK 文件
[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]文件集包括資源可協助您開發、 部署和使用配接器以建立[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。  

## <a name="about-the-sdk"></a>有關 SDK  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是集合的執行階段引擎和工具，可協助配接器開發人員使用 WCF 來建立服務導向的介面，為現有的 LOB 系統。 SDK 的目標是加速的可重複使用、 中繼資料導向，wcf 配接器可讓企業應用程式、 資料庫和傳訊平台整合彼此統一開發。  
  
 此 WCF 架構的 SDK 會呈現為 WCF 繫結至 LOB 系統的配接器。 配接器取用者可以存取配接器類似一般 WCF 服務;若要了解新的程式設計模型沒有取用者。 可以包括自訂的.NET 應用程式的多個.NET 應用程式中重複使用相同的配接器開發[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，SharePoint 和 Microsoft SQL Server Integration Services (SSIS) 透過配接器提供開發人員 – ADO.NET 填充碼。 此外，配接器會提供中繼資料瀏覽、 搜尋和擷取功能。配接器取用者可以選擇性地產生反映 LOB 系統的即時的型別模型的 WCF 合約。  
 
## <a name="readme"></a>讀我檔案
![社群資源圖示](../../adapters-and-accelerators/adapter-oracle-database/media/community.gif "社群")[讀我檔案和隱私權](../../adapters-and-accelerators/wcf-lob-adapter-sdk/readme-and-privacy-in-the-wcf-lob-adapter-sdk.md)描述的元件隨附於 SDK，以及您說明隱私權選項。 

## <a name="install"></a>Install
![快速入門圖示](../../adapters-and-accelerators/adapter-oracle-database/media/f397b0c1-6fe1-4247-a868-9efcab4a5f55.gif "f397b0c1-6fe1-4247-a868-9efcab4a5f55") [安裝 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/install-the-wcf-lob-adapter-sdk.md)列出安裝和解除安裝 SDK，移除自訂配接器，並執行的步驟無訊息安裝。 

## <a name="get-started"></a>快速入門
![快速入門圖示](../../adapters-and-accelerators/adapter-oracle-database/media/f397b0c1-6fe1-4247-a868-9efcab4a5f55.gif "f397b0c1-6fe1-4247-a868-9efcab4a5f55") [快速入門與 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/get-started-with-the-with-the-wcf-lob-adapter-sdk.md)包含熟悉的使用者部分有用的資訊[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，包括概念性的讀取和某些教學課程。 
  
## <a name="plan-and-design"></a>規劃和設計 
![配接器架構圖示](../../adapters-and-accelerators/adapter-oracle-database/media/4af6a1c5-948f-4bf7-bb56-4d63a47f4825.gif "4af6a1c5-948f-4bf7-bb56-4d63a47f4825") [規劃和設計配接器使用 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)所述使用配接器、 通道或服務的時機. 也支援傳訊模式，設計 URI、 了解的交易，以及更多有關讀取。

## <a name="develop-and-create"></a>開發和建立
![配接器開發圖示](../../adapters-and-accelerators/adapter-oracle-database/media/44af70c9-cab1-4201-9912-d115cbc7e16f.gif "44af70c9-cab1-4201-9912-d115cbc7e16f") [開發，或建立您的配接器使用 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/develop-or-create-your-adapter-using-the-wcf-lob-adapter-sdk.md)列出的一些最佳作法，提供指導方針版本控制、 驗證，等等。

## <a name="gac-and-deploy"></a>GAC 和部署
![配接器範例圖示](../../adapters-and-accelerators/adapter-sap/media/2e8eba6a-6ba1-431e-9e0a-f0f45e036e8a.gif "2e8eba6a-6ba1-431e-9e0a-f0f45e036e8a")建立您的配接器之後下, 一個步驟是將它加入至 GAC，更新 machine.config，並建立部署套件。 [部署配接器使用 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/deploy-adapter-using-the-wcf-lob-adapter-sdk.md)包含這項資訊。

## <a name="troubleshoot"></a>疑難排解
![配接器疑難排解圖示](../../adapters-and-accelerators/adapter-oracle-database/media/383a7392-2eb9-485d-b6a8-0187cd5c709d.gif "383a7392-2eb9-485d-b6a8-0187cd5c709d") [疑難排解配接器使用 WCF LOB 配接器 SDK 建立](../../adapters-and-accelerators/wcf-lob-adapter-sdk/troubleshoot-adapter-created-using-the-wcf-lob-adapter-sdk.md)的步驟來啟用追蹤、 使用的清單效能計數器，而且產生的 WSDL。

