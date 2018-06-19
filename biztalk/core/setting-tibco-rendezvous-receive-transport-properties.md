---
redirect_url: /biztalk/core/creating-tibco-rendezvous-receive-handlers/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: 48eb0c1694168fb1acf840a52dc793d0ed943a19
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24014229"
---
# <a name="setting-tibco-rendezvous-receive-transport-properties"></a>設定 TIBCO Rendezvous 接收傳輸屬性
當您設定 Microsoft BizTalk Adapter for TIBCO Rendezvous 接聽訊息時，需指定要接聽的主體名稱。 這是唯一需要的屬性。  
  
 使用此程序可指定屬性。  
  
## <a name="enter-tibco-rendezvous-transport-properties"></a>輸入 TIBCO Rendezvous 傳輸屬性  
  
1.  在 TIBCO Rendezvous 傳輸屬性 對話方塊中，展開 **配接器必要屬性**，輸入**Rendezvous 主體名稱**。  
  
     這是配接器接聽的主體名稱 (Rendezvous 允許使用萬用字元)。 在最簡單的部署案例中，這是唯一需要的屬性。  
  
     ![](../core/media/sadp-tibcorecvtranspropertiess.gif "SAdp_TIBCORecvTransPropertiess")  
  
2.  在**保證接聽程式設定**，如果您想認證訊息，提供可重複使用的名稱與分類帳檔案名稱。  
  
     如果您要定義分散式佇列，這是必要的。 如果不需要保證傳訊，請將這些項目保留空白。 在此主機上定義的所有連接埠與此主機上執行的其他 TIBCO Rendezvous 程式之間，分類帳檔案名稱與可重複使用的名稱必須是唯一的。 如果不是唯一，使用者介面偵測不出來，但在執行階段會發生並記錄錯誤。  
  
3.  在**分散式佇列設定**，分散式的佇列不是必要項目，則不會變更項目。  
  
     下列值是與 BizTalk Server 群組搭配使用的。 BizTalk Adapter for TIBCO Rendezvous 在對 TIBCO RV 的 API 呼叫中會使用這些值。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**分類帳檔案名稱**|保證接聽程式 (或群組成員) 的分類帳檔案名稱。 預設值是空值。<br /><br /> 如果未指定值，會使用記憶體分類帳。|  
    |**可重複使用的名稱**|可重複使用認證的接聽程式 （或群組成員） 的名稱。 預設值是空值。<br /><br /> 需要可重複使用的名稱，才能在重新啟動處理程序後繼續使用。 如果未指定值，會使用產生的 (非可重複使用) 名稱。|  
  
     如果在 BizTalk Server 群組中部署 TIBCO Rendezvous 接收位置，分散式佇列是很有用的。 如果是那樣的話，請輸入想要的間隔和原則值。 啟用間隔與活動訊號間隔會依原狀提供給 TIBCO Rendezvous。 由於間隔在所有分散式佇列的參與者之間必須是相同的，因此值只需輸入一次。 使用原則時，就可以輕鬆在每個主機上指定不同的值。 所有原則值都依循相同的分號分隔冒號分隔主機:值配對語法。  
  
     例如， **host1:10 host2:20; host3:30**  
  
     主機名稱必須是有效的 DNS 主機名稱或 IP 位址。 對於每個原則，配接器會尋找與它的主機關聯的值，並將該值與 TIBCO Rendezvous API 一起使用。  
  
     如果值相同的所有電腦上，您可以輸入簡單的值，而不是名稱： 值配對的清單 (例如， **20**)。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**啟用間隔**|此分散式佇列所用的排程器加權原則。 這是沒有來自排程器之活動訊號訊息的時間間隔，在此間隔後，TIBCO RV 會啟用新的排程器。 預設值是 20 秒。|  
    |**活動訊號間隔**|此分散式佇列所用的活動訊號間隔。 會與 BizTalk Server 群組參數搭配使用。 BizTalk Adapter for TIBCO Rendezvous 在對 TIBCO RV 的 API 呼叫中會使用這些值。 做為群組的作用中排程器的配接器執行個體會使用此值，並以該間隔 (秒) 廣播活動訊號訊息。 預設值為 10。|  
    |**排程器加權原則**|根據預設 (空值)，群組的所有成員成為排程器的機會均相等。 主機-加權配對值清單提供不同的加權原則。 預設值是空值。|  
    |**工作者產能原則**|此分散式佇列所用的工作者產能原則。 此值表示群組成員可處理多少個並行工作。 如果未指定，預設值為 1。 主機-產能配對值清單提供不同的產能原則。|  
    |**工作者加權原則**|此分散式佇列所用的工作者加權原則。 此值提供一個加權值，以協助 TIBCO 在分散式佇列中指派工作。 可用的工作者會優先被指派加權值較高的工作。 預設值為 1。|  
  
4.  展開**一般設定**並輸入 TIBCO Rendezvous 伺服器連線的所有必要的資訊。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**附錄萬用字元替代值**|指定萬用字元文字替代值。 在產生的訊息中，是使用接收位置接聽的主體名稱來產生 XML 目標命名空間。 根據預設，配接器會將產生的訊息中的任何 '>' 萬用字元取代為 GTWILDCARD 文字。 您可以在此欄位中指定不同的萬用字元。|  
    |**字碼頁編號**|識別訊息建立者編碼包含於內送訊息中之字串所用的字碼頁。 預設值為 65001。 （此配接器不支援具有從兩個不同的字碼頁環境產生相同訊息物件。）|  
    |**項目萬用字元替代值**|指定不同的萬用字元文字替代值。在產生的訊息中，是使用接收位置接聽的主體名稱來產生 XML 目標命名空間。 根據預設，配接器會將產生的訊息中的任何 '*' 萬用字元取代為 STARWILDCARD 文字。 您可以在此欄位中指定不同的萬用字元。|  
    |**事件佇列名稱**|指定當您建立 Rendezvous 佇列物件時要使用的名稱。 這是為便於使用而提供，因為關聯的記錄訊息會顯示事件佇列名稱。 預設值是空白。|  
    |**篩選**|當您在接聽的主體名稱中指定萬用字元時，目標協調流程可能只會對可能到達的極大型主體集合的子集感興趣。 為了將對 BizTalk Server 的影響降至最低以及盡量減少相關資料庫存取活動，您可以進一步指定應傳送至 BizTalk Server 的訊息。 此項目包含以分號分隔的主體名稱清單 (不允許萬用字元)。 使用萬用字元主體名稱 (但主體名稱在此清單中) 的任何訊息都將被篩除 (不傳送至 BizTalk Server)。 在篩選器值前面加上 '!' 字元，可反轉篩選器邏輯。 預設值是空白 (無篩選器)。|  
    |**將不受支援的型別對應至字串**|不支援的類型應產生錯誤或對應至字串。 如果使用配接器搭配已新增類型的較新版 TIBCO Rendezvous 時，就可使此項目。|  
    |**BizTalk 群組的成員**|如果設定為 True，必須設定分散式佇列參數 (參考 [分散式佇列設定] 節點) 與保證接聽程式參數 (參考 [認證接聽程式設定] 節點)。 預設值是 False。|  
    |**路徑**|設定為指向 TIBCO Rendezvous 二進位檔案 (如果該資訊不在 PATH 環境變數中的話)。|  
    |**保留順序**|配接器是否以收到內送訊息的順序將它們發送到 BizTalk Server (例如，使用單一發送器執行緒)。 請注意，如果未設定保證傳訊參數，不表示配接器是以訊息傳送的順序接收訊息 (指的是單一來源)。|  
    |**接收位置識別碼**|接收位置的名稱。|  
    |**保留**|針對特殊用途保留的欄位。|  
  
5.  展開**Rendezvous 傳輸**，然後輸入 TIBCO Rendezvous 精靈與程式之間通訊的所有必要的資訊。  
  
     **傳輸 （網路服務精靈，服務）** 指定 TIBCO Rendezvous 精靈交換訊息的方式。 這些設定會依原狀傳送至 TIBCO Rendezvous API。 使用預設值 (空白) 則會使用預設的通訊策略。  
  
     TIBCO Rendezvous 傳輸定義了傳遞領域，也就是它所傳送之訊息可能的目的地集合。 此屬性集定義一個傳輸。  
  
    |參數|Description|  
    |---------------|-----------------|  
    |**精靈**|輸入 Rendezvous 傳輸精靈參數的數值識別碼。|  
    |**網路**|輸入 Rendezvous 網路參數的名稱。|  
    |**服務名稱**`e`|輸入 Rendezvous 傳輸服務的名稱。|  
  
6.  提供使用單一登入 (SSO) 的認證。  
  
     您可以使用兩種方法來存取 TIBCO Rendezvous 系統。 您可以使用認證 (使用者名稱和密碼參數) 或單一登入。  
  
    1.  選取**是**中**使用 SSO**使用單一登入。  
  
        > [!NOTE]
        >  請參閱[安全性](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)如需有關如何設定 SSO 資訊。  
  
    2.  從清單中選取一個分支機構應用程式。  
  
         企業單一登入工具建立的分支機構應用程式代表一個應用程式 (例如 TIBCO Rendezvous)。 Microsoft BizTalk Adapter for TIBCO Rendezvous 會使用應用程式使用者的認證。 這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 資料庫中擷取所得。  
  
        > [!NOTE]
        >  如需如何建立分支機構應用程式資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications1.md)。  
  
7.  提供所有必要的資訊之後, 按一下**套用**，然後按一下 **確定**。  
  
     您必須為 BizTalk Adapter for TIBCO Rendezvous 設定連線參數，以接收 TIBCO Rendezvous 訊息。  
  
## <a name="see-also"></a>另請參閱  
 [建立 TIBCO Rendezvous 接收處理常式](../core/creating-tibco-rendezvous-receive-handlers.md)