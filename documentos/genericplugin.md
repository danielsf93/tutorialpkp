PLUGIN GENÉRICO TROCA DE LAYOUT

plugins/generic/layout
                 |   |-index.php
                 |   |-manifest.xml
                 |   |-version.xml
                 |   |-PLUGIN.php
                 |   
                 |---templates/frontend/objects
                 |                          |-article_details.tpl
                 |                
                 |---locale/pt_BR
                              |-locale.po


HookRegistry TemplateResource
https://docs.pkp.sfu.ca/dev/plugin-guide/3.3/en/templates
https://docs.pkp.sfu.ca/ojs-2-technical-reference/en/variables

Sobreposição/Renderização de template html

Por padrão, um arquivo de modelo em um plugin de tema que corresponda ao caminho de um arquivo de modelo no aplicativo irá substituí-lo. Você pode conceder essa capacidade a qualquer plugin.
Adicione um gancho durante o registro para permitir que os modelos de um plugin substituam os modelos na aplicação.

-----------------------------------
class layout extends GenericPlugin {
    public function register($category, $path, $mainContextId = NULL) {
        $success = parent::register($category, $path);
            if ($success && $this->getEnabled()) {
               HookRegistry::register('TemplateResource::getFilename', array($this, '_overridePluginTemplates'));
    
            }
        return $success;
    }
----------------------------------
//sobreposição de arquivo da página do artigo
	public function _overridePluginTemplates($hookName, $args) {
		$templatePath = $args[0];
		if ($templatePath === 'templates/frontend/objects/article_details.tpl') {
			$args[0] = 'plugins/generic/viewcounter/templates/frontend/objects/article_details.tpl';
		}
		return false;
	}
----------------------------------

Total de visualizações de um artigo(subtitle): {$article->getViews()}
Arte: <i class='fa fa-bar-chart' style='color: red'></i> (https://fontawesome.com/v4/icons/)

Total de Downloads{* Article Galleys *}:{$galley->getViews()}
Arte: <i class='fa fa-download' style='color: red'></i>

Complementares {if $supplementaryGalleys}:{$galley->getViews()}
Arte: <i class='fa fa-download' style='color: red'></i>

----------------------------------
Gerar link de pesquisa com o nome do autor dentro da própria revista
{$author->getFullName()|escape}

link de pesquisa
http://0.0.0.0:8888/index.php/geousp/search/search?query=&dateFromYear=&dateFromMonth=&dateFromDay=&dateToYear=&dateToMonth=&dateToDay=&authors=(AUTOR)

link de pesquisa simplificado
http://0.0.0.0:8888/index.php/geousp/search/search?query=&authors=(AUTOR)
{url page="search" router=$smarty.const.ROUTE_PAGE}/search?query=&authors=

<span class="name">
	<a href="{url page="search" router=$smarty.const.ROUTE_PAGE}/search?query=&authors={$author->getFullName()|escape}">{$author->getFullName()|escape}</a>



