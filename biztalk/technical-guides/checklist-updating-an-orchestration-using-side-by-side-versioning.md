---
title: "檢查清單： 更新協調流程中使用的並存版本控制 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97f66987-0269-4dfe-a648-7b68412e86fe
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 110eb0df6373d8679fed0431c91d10a6633e0610
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-updating-an-orchestration-using-side-by-side-versioning"></a>檢查清單： 更新協調流程中使用的並存版本控制
變更協調流程可以更為複雜，比其他成品，例如對應變更。 如果您有存留較短的協調流程，簡單的更新可能不足。 但是，如果您有長時間執行的協調流程，或無法終止現有的執行個體，則-並存版本控制會是唯一的選擇。  
  
 當協調流程處理長時間執行的交易時，您無法立即變更為更新版本的協調流程。 您必須允許原始的版本，以完成處理訊息，因此不會遺失。 若要完成這項作業，您要將更新的協調流程部署到與原始版本相同的應用程式中。 然後再停止原始的版本，並啟動更新版本使它可以接收所有新的訊息，而舊版本則持續處理任何已傳遞的訊息。 在原始的協調流程完成所有其訊息的處理之後，請將它從部署所在的 BizTalk 應用程式中解除部署。  
  
|步驟|參考|  
|-----------|---------------|  
|必要的變更協調流程後，遞增組件版本號碼。|[如何更新組件](../technical-guides/how-to-update-an-assembly.md)|  
|部署到 BizTalk 應用程式，從 Visual Studio 組件，然後測試組件。 **注意：**請確定您選取要在 GAC 中安裝組件的部署選項。|[部署 BizTalk 組件從 Visual Studio 到 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=154719)(http://go.microsoft.com/fwlink/?LinkID=154719)。|  
|將組件匯出至.msi 檔案將測試環境中的應用程式。|[如何匯出至.msi 檔案的應用程式](../technical-guides/how-to-export-an-application-to-an-msi-file.md)|  
|將.msi 檔案匯入實際執行環境，其中包含您想要更新的協調流程的 BizTalk 應用程式。 **注意：**您可以使用下列步驟的測試組件並將其部署到實際執行環境。|[如何從.msi 檔案匯入應用程式](../technical-guides/how-to-import-an-application-from-an-msi-file.md)|  
|繫結更新與原始協調流程使用相同的繫結的協調流程。|[如何設定協調流程的繫結](http://go.microsoft.com/fwlink/?LinkId=154850)(http://go.microsoft.com/fwlink/?LinkId=154850)。|  
|取消登錄原始的協調流程，然後啟動更新的協調流程。 **注意：**避免任何訊息遺失，您應該執行下列作業以程式設計的方式。|如需有關以程式設計方式部署協調流程的詳細資訊，請參閱[部署和啟動新版本的協調流程以程式設計方式](http://go.microsoft.com/fwlink/?LinkId=154851)(http://go.microsoft.com/fwlink/?LinkId=154851)。<br /><br /> 如需有關如何手動部署協調流程的詳細資訊，請參閱中的下列[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]協助：<br /><br /> -   [如何取消登錄協調流程](http://go.microsoft.com/fwlink/?LinkId=154852)(http://go.microsoft.com/fwlink/?LinkId=154852)。<br />-   [如何登錄協調流程](http://go.microsoft.com/fwlink/?LinkId=154853)(http://go.microsoft.com/fwlink/?LinkId=154853)。<br />-   [如何啟動協調流程](http://go.microsoft.com/fwlink/?LinkId=154854)(http://go.microsoft.com/fwlink/?LinkId=154854)。|  
|監視系統執行個體的原始的協調流程版本使用 群組中樞頁面上的查詢檢視。|[如何檢視協調流程的執行個體資訊](http://go.microsoft.com/fwlink/?LinkId=154855)(http://go.microsoft.com/fwlink/?LinkId=154855)。|  
|所有其作用中、 凍結和擱置的執行個體完成時，解除部署應用程式從原始的協調流程。|[如何從應用程式移除協調流程](http://go.microsoft.com/fwlink/?LinkId=154856)(http://go.microsoft.com/fwlink/?LinkId=154856)。|  
|從每部執行應用程式的電腦上的 GAC，選擇性地解除安裝的原始組件版本。|[如何從 GAC 解除安裝組件](http://go.microsoft.com/fwlink/?LinkId=154857)(http://go.microsoft.com/fwlink/?LinkId=154857)。|  
  
## <a name="binding-to-receive-ports-and-locations"></a>繫結至接收埠和位置  
 如果您想要建立新接收埠和協調流程的新版本的位置，只要繫結至新的連接埠並登記/啟動新的成品將通常足以。 建立新的接收位置和連接埠通常是慣用的方法，特別是當您的案例使用長時間執行的協調流程的數字的情況下相互關聯接收仍需要進行處理。 在此情況下，您可能無法重複使用現有的接收埠，或執行 unenlistment。 如果您建立新的連接埠，請務必也可處理這項變更讓後端和協力廠商系統。 如果沒有，您必須等候所有長時間執行的執行個體，以做為目標，然後再升級。  
  
 如果您想要使用現有的連接埠，請執行下列動作：  
  
1.  將新版本的協調流程繫結至現有的連接埠。  
  
2.  取消登錄 （但不是會停止） 舊的協調流程版本。  
  
3.  登錄並啟動新的協調流程版本。  
  
    > [!NOTE]  
    >  您可以使用指令碼執行步驟 2 和 3 中一個交易，使訊息不會遺失之間手動按一下訂用帳戶。