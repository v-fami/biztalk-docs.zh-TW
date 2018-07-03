---
title: 測試對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 265afd62-3c1d-4b9a-9f51-176b9b079241
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ad35dd513375f8221ed909fd7f353fc5e6673c7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983935"
---
# <a name="testing-a-map"></a>測試對應
您可以在設計階段測試 EDI 專案中的對應。 若要執行此動作，請在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境中使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的 XML 工具延伸模組。 本主題描述如何設定和使用**測試對應**XML 工具延伸模組的功能。  
  
 您可透過指定來源文件和指定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將儲存所產生執行個體 (與虛構資料) 的資料夾來測試對應。 您必須設定分隔符號，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將用以處理來源文件，並產生目的文件，以根據 EDI 結構描述。 這適用於所有值**TestMap**輸入對應的屬性頁中的屬性：**產生的執行個體**， **XML**，或**原生**。 它適用於**產生的執行個體**因為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]必須知道要用來產生執行個體的分隔符號。 它適用於**XML**或是**原生**因為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]必須知道如何解譯原生的一般檔案或 XML 檔案。 您也需要設定的分隔符號，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會使用產生的輸出檔。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-test-a-map"></a>測試對應  
  
1. 在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]、 新增您想要加入專案中，測試對應及對應的來源和目的地結構描述加入專案。  
  
   > [!NOTE]
   >  您不必建置專案來測試對應。  
  
2. 以滑鼠右鍵按一下地圖，然後按一下 **屬性**。  
  
3. 在 **屬性**視窗中，將**驗證 TestMap 輸入**來 **，則為 True**如果您想要驗證輸入的檔，針對來源結構描述。 設定**驗證 TestMap 輸出**要 **，則為 True**如果您想要驗證輸出檔，針對目的結構描述。  
  
   > [!NOTE]
   >  如果您在測試對應與**TestMap 輸入**屬性設定為**原生**並**驗證 TestMap 輸入**並**驗證 TestMap 輸出**屬性設定為**False**，仍然會進行驗證。 這是因為原生格式的輸入的檔案將轉換成 XML 格式，和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會針對驗證 XML 結構描述。 如果輸入的執行個體中有驗證問題，請驗證機制仍然會公佈錯誤，即使**驗證 TestMap 輸入**並**驗證 TestMap 輸出**屬性會設為 **，則為 false**。  
  
4. 設定**TestMap 輸入**要**原生**為副檔名為.edi 的輸入檔。 將它設定為**XML**如果它具有.xml 副檔名。 設定**TestMap 輸入**要**產生的執行個體**有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]產生輸入執行個體，而不是您以手動方式指定輸入執行個體。  
  
5. 設定**TestMap Output**要**原生**的副檔名為.edi 的輸出檔。 將它設定為**XML**如果它具有.xml 副檔名。  
  
6. 針對**TestMap Input Instance**，瀏覽至您想要用來測試對應，請選取它，輸入執行個體，然後**開啟**。 如果您想要將此屬性保留空白，將**TestMap 輸入**要**產生的執行個體**。  
  
   > [!NOTE]
   >  您不必指定輸入執行個體**TestMap Input Instance**或設定**TestMap 輸入**來**產生執行個體**。 如果沒有，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會產生錯誤。  
  
7. 針對**TestMap 輸出執行個體**，瀏覽至您想要儲存輸出執行個體，輸入輸出執行個體的名稱，然後按一下位置**儲存**。  
  
   > [!NOTE]
   >  如果您未指定輸出執行個體，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將會建立輸出檔、 將輸出檔案放入資料夾，並指出檔案名稱和路徑。  
  
8. 以滑鼠右鍵按一下您要測試，然後再按一下的地圖**測試對應**。  
  
9. 在 X12 **EDI 執行個體屬性**對話方塊方塊中，請確定所有屬性都是一致的輸入和輸出執行個體的設定。  
  
   > [!NOTE]
   >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將會顯示**EDI 執行個體屬性**對話方塊在 TestMap 處理期間，兩次： 一次解譯輸入的訊息執行個體，一次產生輸出訊息執行個體。 不過，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可能會顯示對話方塊兩次以上，而且可以顯示對話方塊中，針對非 EDI 結構描述。 如果是的話，按一下**確定**以關閉對話方塊。  
  
10. 按一下 [確定] 。  
  
## <a name="see-also"></a>另請參閱  
 [使用設計階段 XML 工具](../core/using-design-time-xml-tools.md)