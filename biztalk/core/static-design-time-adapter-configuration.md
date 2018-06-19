---
title: 靜態設計階段配接器組態 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 332723a4-e39d-43f5-af4d-bf9f56496535
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8337e4f53afe22ccbde0e1d1d2a6437d280011d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278894"
---
# <a name="static-design-time-adapter-configuration"></a>靜態設計階段配接器組態
配接器的設計階段部分必須負責定義所有可用屬性並驗證使用者輸入。 在靜態設計階段組態中，配接器使用預設使用者介面 (UI) 來顯示和編輯其屬性。  
  
 本節說明如何實作自訂配接器的靜態設計階段組態功能。 您所決定進行的變更，將會根據配接器與應用程式通訊的需要，以及配接器所需要實作的邏輯。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]「說明」章節的連結，會以更多細節描述這些步驟，或是提供額外的背景資訊 (如果存在)。 此外，它還會叫出範例檔配接器文件中提供相關範例的位置。  
  
## <a name="guidelines-for-the-static-development-process"></a>靜態開發程序的指導方針  
 下列清單提供將靜態設計階段功能建置到配接器中的建議。 在開發期間，您可能不需要進行所有這些步驟，也不需以固定的順序執行它們。  
  
1.  建立配接器組態需求以及需要設定之組態參數的清單。 如果參數要讓所有接收位置和傳送埠在全域使用，請在處理常式結構描述組態檔中指定它們。 如果它們有特定的連接埠或位置，請在傳送埠和接收位置組態檔中予以設定。  
  
2.  修改配接器屬性頁以納入任何新的組態參數。 如需這個步驟的資訊，請參閱[配接器組態結構描述](../core/adapter-configuration-schemas.md)。  
  
3.  使用 [新增配接器中繼資料精靈] 修改結構描述類別的樹狀檢視。 如需有關此步驟的詳細資訊，請參閱[新增配接器中繼資料精靈 中的結構描述類別](../core/schema-categories-in-the-add-adapter-metadata-wizard.md)  
  
4.  修改範例程式碼，將結構描述傳回為 Web 服務描述語言 (WSDL) 檔案。 如需有關此步驟的詳細資訊，請參閱[靜態配接器 IStaticAdapterConfig 介面](../core/static-adapter-istaticadapterconfig-interface.md)。  
  
5.  修改現有的 WSDL 檔案或建立新的 WSDL 檔案。 如需有關此步驟的詳細資訊，請參閱[配接器 WSDL 檔案](../core/adapter-wsdl-files.md)。  
  
6.  修改範例程式碼，傳回配接器所需要卻未包含在 WSDL 檔案中的其他 XSD 檔案。 如需有關此步驟的詳細資訊，請參閱[配接器 GetSchema 方法](../core/adapter-getschema-method.md)。  
  
7.  修改配接器登錄機碼並執行配接器登錄檔。 如需有關此步驟的詳細資訊，請參閱[配接器登錄檔案](../core/adapter-registration-file.md)。  
  
8.  將靜態配接器安裝到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 如需有關此步驟的詳細資訊，請參閱[配接器安裝到 BizTalk Server](../core/install-the-adapter-into-biztalk-server.md)。  
  
9. 測試對配接器屬性頁進行的變更。 重新建置配接器，測試出現在 [新增配接器中繼資料精靈] 中的 UI。 如需有關此步驟的詳細資訊，請參閱[建置和測試配接器專案](../core/build-and-test-the-adapter-project.md)  
  
## <a name="in-this-section"></a>本節內容  
  
-   [靜態配接器 IStaticAdapterConfig 介面](../core/static-adapter-istaticadapterconfig-interface.md)  
  
-   [結構描述中的類別目錄新增配接器中繼資料精靈](../core/schema-categories-in-the-add-adapter-metadata-wizard.md)