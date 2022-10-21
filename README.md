# THINGS IN HERE

## GEMS

```
gem "sassc-rails"
gem 'simple_form'
gem 'haml'
# gem 'bootstrap-sass'
```
- sassc for scss
- simple form
- i didnt use botstrap

## MODELS
- categories have many tasks
- task belongs to categories
- filter tasks by category on the homepage

```
%ul.nav.navbar-nav
	%li= link_to "All Tasks", root_path
	- Category.all.each do |category|				
		%li= link_to category.name, tasks_path(category: category.name)
= link_to "New Task", new_task_path, class: "navbar-text navbar-right navbar-link"
```

- and in the controller

```
  def index
    if params[:category].blank?
      @tasks = Task.all.order("created_at DESC")
    else
      @category_id = Category.find_by(name: params[:category]).id
      @tasks = Task.where(category_id: @category_id).order("created_at DESC")
    end
  end
```

## OTHER
- custom styling with bootstrap
