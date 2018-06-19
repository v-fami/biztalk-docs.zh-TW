---
title: 步驟 2： 分類的介面卡和連接屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45b3dc64-2078-4008-878b-501f727f4a11
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e9d49323695b1070a8065cf7a5e548e61fc5db9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22226822"
---
# <a name="step-2-categorize-the-adapter-and-connection-properties"></a>步驟 2： 分類的介面卡和連接屬性
![步驟 2 的 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-2of9.gif "Step_2of9")  
  
 **若要完成的時間：** 30 分鐘  
  
 在此步驟中，您會更新**EchoAdapterBindingElement**和**EchoAdapterBindingElementExtensionElement**類別來指定您的配接器和連接屬性的類別。 如此一來，屬性會以邏輯方式分組中依分類[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]工具。 比方說，如果您想要**應用程式**， **EnableAuthentication**，和**Hostname**屬性下方出現**連接**類別如下所示，您需要將連接類別指派給每個應用程式、 EnableAuthentication 及主機名稱的屬性。  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/c7c0c013-6651-4c32-9f8b-b546a68a0267.gif "c7c0c013-6651-4c32-9f8b-b546a68a0267")  
  
 同樣地，如果您想**InboundFileFilter**和**InboundFleSystemWatcherFolder**屬性下方出現**輸入**類別如下所示，您需要為每個指派輸入類別目錄。 如果您想**計數**和**EnableConnectionPooling**下方出現**其他**分類中，您需要為每個指派其他類別目錄。  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/2acb7677-8b50-4e45-96a3-42d0e2011f19.gif "2acb7677-8b50-4e45-96a3-42d0e2011f19")  
  
 請記住，您可以指定具有您所選擇的任何類別目錄名稱的屬性。 在此範例中，因為 EnableConnnectionPooling 屬性不屬於其他類別，我們將分類它做為其他 （其他）。 對於 InboundFileFilter 屬性中，因為它用在此範例中，輸入處理期間則會更適當地將輸入指派給屬性，而不是其他。 以下是回應配接器為完整的自訂屬性分類。  
  
|**屬性**|**類別目錄**|  
|------------------|------------------|  
|InboundFileFilter|輸入|  
|InboundFileSystemWatcherFolder|輸入|  
|Count|其他|  
|EnableConnectionPooling|其他|  
|應用程式|連接|  
|EnableAuthentication|連接|  
|主機名稱|連接|  
|EchoInUpperCase|格式|  
  
 除了這些變更，您也修改的 Dispose 方法**EchoAdapterHandlerBase**。  
  
 如回應配接器所公開的配接器屬性，請參閱配接器的 properties 區段[教學課程 1： 開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)。  
  
## <a name="prerequisites"></a>必要條件  
 在開始此步驟之前，必須先完成[步驟 1： 使用 WCF LOB 配接器開發精靈來建立回應配接器專案](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-wcf-lob-adapter-development-wizard-to-create-the-echo-adapter.md)。 您也應該熟悉`System.ServiceModel.Configuration.BindingElementExtensionElement`和`System.ServiceModel.Configuration.StandardBindingElement`類別。  
  
## <a name="update-the-echoadapterhandlerbase-dispose-method"></a>更新 EchoAdapterHandlerBase Dispose 方法  
  
1.  在**方案總管 中**，連按兩下**EchoAdapterHandlerBase.cs**檔案。  
  
2.  移除下列陳述式從**處置**方法：  
  
    ```csharp  
    throw new NotImplementedException("The method or operation is not implemented.");  
    ```  
  
     修改過的方法看起來應該如下所示：  
  
    ```csharp  
    protected virtual void Dispose(bool disposing)  
    {  
       //  
       //TODO: Implement Dispose. Override this method in respective Handler classes  
       //  
    }  
    ```  
  
## <a name="update-the-adapter-properties-class"></a>更新配接器屬性類別  
  
1.  在**方案總管 中**，連按兩下**EchoAdapterBindingElement.cs**檔案。  
  
2.  在 Visual Studio 編輯器中，展開 **自訂產生屬性**區域。  
  
3.  若要指派**其他**類別**計數**屬性，加入下列單一陳述式的開頭**計數**實作。  
  
    ```csharp  
    [System.ComponentModel.Category("")]  
    ```  
  
     **計數**實作現在應符合下列：  
  
    ```csharp  
    [System.ComponentModel.Category("")]  
    [System.Configuration.ConfigurationProperty("count", DefaultValue = 5)]  
    public int Count  
    {  
        get  
        {  
            return ((int)(base["Count"]));  
        }  
        set  
        {  
            base["Count"] = value;  
        }  
    }  
    ```  
  
4.  若要指派**其他**類別**EnableConnectionPooling**屬性，加入下列單一陳述式的開頭**EnableConnectionPooling**實作。  
  
    ```csharp  
    [System.ComponentModel.Category("")]  
    ```  
  
5.  若要指派**輸入**類別**InboundFileFilter**屬性，加入下列單一陳述式的開頭**InboundFileFilter**實作。  
  
    ```csharp  
    [System.ComponentModel.Category("Inbound")]  
    ```  
  
6.  若要指派**輸入**categoryto **inboundFleSystemWatcherFolder**屬性，加入下列單一陳述式的開頭**inboundFleSystemWatcherFolder**實作。  
  
    ```csharp  
    [System.ComponentModel.Category("Inbound")]  
    ```  
  
7.  請確認程式碼中的核取**自訂產生屬性**區符合下列：  
  
    ```csharp  
    [System.ComponentModel.Category("")]  
    [System.Configuration.ConfigurationProperty("count", DefaultValue = 5)]  
    public int Count  
    {  
        get  
        {  
            return ((int)(base["Count"]));  
        }  
        set  
        {  
            base["Count"] = value;  
        }  
    }  
  
    [System.ComponentModel.Category("")]  
    [System.Configuration.ConfigurationProperty("enableConnectionPooling", DefaultValue = true)]  
    public bool EnableConnectionPooling  
    {  
        get  
        {  
            return ((bool)(base["EnableConnectionPooling"]));  
        }  
        set  
        {  
            base["EnableConnectionPooling"] = value;  
        }  
    }  
  
    [System.ComponentModel.Category("Inbound")]  
    [System.Configuration.ConfigurationProperty("inboundFileFilter", DefaultValue = "*.txt")]  
    public string InboundFileFilter  
    {  
        get  
        {  
            return ((string)(base["InboundFileFilter"]));  
        }  
        set  
        {  
            base["InboundFileFilter"] = value;  
        }  
    }  
  
    [System.ComponentModel.Category("Inbound")]  
    [System.Configuration.ConfigurationProperty("inboundFileSystemWatcherFolder", DefaultValue = "{InboundFileSystemWatcherFolder}")]  
    public string InboundFileSystemWatcherFolder  
    {  
        get  
        {  
            return ((string)(base["InboundFileSystemWatcherFolder"]));  
        }  
        set  
        {  
            base["InboundFileSystemWatcherFolder"] = value;  
        }  
    }  
  
    #endregion Custom Generated Properties  
    ```  
  
## <a name="update-the-connection-properties"></a>更新連接屬性  
  
1.  在**方案總管 中**，連按兩下**EchoAdapterConnectionUri.cs**檔案。  
  
2.  在 Visual Studio 編輯器中，展開 **自訂產生屬性**區域。  
  
3.  若要指派**格式**類別**EchoInUpperCase**屬性，加入下列單一陳述式的開頭**EchoInUpperCase**實作。  
  
    ```csharp  
    [System.ComponentModel.Category("Format")]  
    ```  
  
4.  若要指派**連接**類別**Hostname**屬性，開頭新增下列單一陳述式**主機名稱**實作。  
  
    ```csharp  
    [System.ComponentModel.Category("Connection")]  
    ```  
  
5.  若要指派**連接**類別**應用程式**屬性，新增下列單一陳述式的開頭**應用程式**實作。  
  
    ```csharp  
    [System.ComponentModel.Category("Connection")]  
    ```  
  
6.  若要指派**連接**categoryto **EnableAuthentication**屬性，加入下列單一陳述式的開頭**EnableAuthentication**實作。  
  
    ```csharp  
    [System.ComponentModel.Category("Connection")]  
    ```  
  
7.  請確認程式碼中的核取**自訂產生屬性**區符合下列：  
  
    ```csharp  
    #region Custom Generated Properties  
            [System.ComponentModel.Category("Format")]  
            public bool EchoInUpperCase  
            {  
                get  
                {  
                    return this.echoInUpperCase;  
                }  
                set  
                {  
                    this.echoInUpperCase = value;  
                }  
            }  
  
            [System.ComponentModel.Category("Connection")]  
            public string Hostname  
            {  
                get  
                {  
                    return this.hostname;  
                }  
                set  
                {  
                    this.hostname = value;  
                }  
            }  
  
            [System.ComponentModel.Category("Connection")]  
            public string Application  
            {  
                get  
                {  
                    return this.application;  
                }  
                set  
                {  
                    this.application = value;  
                }  
            }  
  
            [System.ComponentModel.Category("Connection")]  
            public bool EnableAuthentication  
            {  
                get  
                {  
                    return this.enableAuthentication;  
                }  
                set  
                {  
                    this.enableAuthentication = value;  
                }  
            }  
            #endregion Custom Generated Properties  
    ```  
  
8.  在 Visual Studio 中，從**檔案**功能表上，按一下 **全部儲存**。  
  
> [!NOTE]
>  您應該已經儲存您的工作結果。 您可以安全地關閉目前的 Visual Studio 或移至下一個步驟中，[步驟 3： 實作 Echo 介面卡的連線](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md)。  
  
## <a name="what-did-i-just-do"></a>我剛剛做什麼？  
 剛更新的類別，以回應配接器所公開的每個配接器和連接屬性中指定的類別。  
  
## <a name="next-steps"></a>後續步驟  
 您可以實作連接、 中繼資料瀏覽、 搜尋和解析功能，以及輸出的訊息交換。 最後，您會建置並部署回應配接器。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3： 實作 Echo 介面卡的連線](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md)   
 [教學課程 1： 在開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)