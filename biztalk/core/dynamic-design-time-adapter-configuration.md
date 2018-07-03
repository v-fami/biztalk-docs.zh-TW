---
title: 動態設計階段配接器組態 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 36127d62-0348-42bb-981f-19fcad26efce
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e54d45c920fa430880e7a51d66ae500bfa9e13af
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988143"
---
# <a name="dynamic-design-time-adapter-configuration"></a>動態設計階段配接器組態
在某些狀況下，靜態設計階段配接器組態和 [新增配接器中繼資料精靈] 中的標準預設 UI，並沒有顯示配接器要匯入之 BizTalk 專案服務的足夠彈性。 或者，您可以使用動態設計階段組態，在其中提供精靈的自訂 UI 以顯示和選取配接器的服務。 BizTalk 配接器架構提供一組 API，可以讓您用來匯入配接器所需要的結構描述，並能顯示自訂的 UI。  
  
 本節說明如何實作自訂配接器的動態設計階段組態功能。 您所決定進行的變更，將會根據配接器與應用程式通訊的需要，以及配接器所需要實作的邏輯。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]「說明」章節的連結，會以更多細節描述這些步驟，或是提供額外的背景資訊 (如果存在)。 此外，它還會叫出範例檔配接器文件中提供相關範例的位置。  
  
## <a name="guidelines-for-the-dynamic-development-process"></a>動態開發程序的指導方針  
 下列清單提供將動態設計階段功能建置到配接器中的建議。 在開發期間，您可能不需要進行所有這些步驟，也不需要以固定的順序執行它們。  
  
1. 建立配接器組態需求以及需要設定之組態參數的清單。 如果參數要讓所有接收位置和傳送埠在全域使用，請在處理常式結構描述組態檔中指定它們。 如果它們有特定的連接埠或位置，請在傳送埠和接收位置組態檔中予以設定。  
  
2. 修改配接器屬性頁以納入任何新的組態參數。 如需此步驟的詳細資訊，請參閱[配接器組態結構描述](../core/adapter-configuration-schemas.md)。  
  
3. 為 [新增配接器中繼資料精靈] 建立自訂使用者介面 (UI)，以便選取新增至專案的結構描述。 在此列出的所有建議中，只有這項會區別動態與靜態配接器。 如需有關此步驟的詳細資訊，請參閱 <<c0> [ 動態配接器 DisplayUI 方法](../core/dynamic-adapter-displayui-method.md)和類別[Microsoft.BizTalk.Adapter.Framework.IDynamicAdapterConfig.DisplayUI](http://msdn.microsoft.com/library/microsoft.biztalk.adapter.framework.idynamicadapterconfig.displayui.aspx)。  
  
4. 修改範例程式碼，將結構描述傳回為 Web 服務描述語言 (WSDL) 檔案。 如需有關此步驟的詳細資訊，請參閱 <<c0> [ 靜態配接器 IStaticAdapterConfig 介面](../core/static-adapter-istaticadapterconfig-interface.md)。  
  
5. 修改現有的 WSDL 檔案或建立新的 WSDL 檔案。 如需有關此步驟的詳細資訊，請參閱 <<c0> [ 配接器 WSDL 檔案](../core/adapter-wsdl-files.md)。  
  
6. 修改範例程式碼，傳回配接器所需要卻未包含在 WSDL 檔案中的其他 XSD 檔案。 如需有關此步驟的詳細資訊，請參閱 <<c0> [ 配接器 GetSchema 方法](../core/adapter-getschema-method.md)。  
  
7. 修改配接器登錄機碼並執行配接器登錄檔。 如需有關此步驟的詳細資訊，請參閱 <<c0> [ 配接器登錄檔案](../core/adapter-registration-file.md)。  
  
8. 將靜態配接器安裝到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 如需有關此步驟的詳細資訊，請參閱 <<c0> [ 配接器安裝到 BizTalk Server](../core/install-the-adapter-into-biztalk-server.md)。  
  
9. 測試對配接器屬性頁進行的變更。 重新建置配接器，測試出現在 [新增配接器中繼資料精靈] 中的 UI。 如需有關此步驟的詳細資訊，請參閱[建置和測試配接器專案](../core/build-and-test-the-adapter-project.md)  
  
## <a name="in-this-section"></a>本節內容  
  
-   [動態配接器 DisplayUI 方法](../core/dynamic-adapter-displayui-method.md)